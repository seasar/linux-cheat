File compression formats and utilities.

The performance parameters are:

- compression ratio
- compression time
- can see and extracting single files
- support across OS
- ability to break into chunks
- keep file metadata such as permissions, hidden (windows), etc.

# zip

most widely supported format

not so high compression

easy to view and extract single files

compresses dir file by file it seems

zip file or directory

    zip -r "$F".zip "$F"

-r : add dir recursivelly. otherwise, adds only the top dir!

-e : encrypt:

    zip -er "$F".zip "$F"

you can still see filenames!! but not extract them

list all files in zip file

    unzip -l "$F".zip

extract files from zip:

    unzip "$F".zip

if has password, asks for it

to a dir

    unzip "$F".zip -d out

    for F in *; do echo "$F"; echo "$F".zip; zip "$F".zip "$F"; done
zip every file in cur dir to file.zip

# tar tar.gz tgz tar.bz2 tb2

tar only turns dir into file, but no compression

this is why it is often coupled with gz and bz2: those are files compressers

gz gives similar compression to .zip

gz2 gives more compression than gz (30% for roms), but MUCH slower to make, and you can't extract individual files easily.

tgz == tar.gz
txz == tar.xz
tb2 == tbz == tar.bz2

create

    tar vcf "$F".tar "$F"
    tar vczf "$F".tgz "$F"
    tar vcjf "$F".tbz "$F"
    tar vcJf "$F".txz "$F"

- c: create
- f: to file given as next arg, not to stdout
- z: gzip
- j: bzip2
- v: verbose

extract:

    tar vxf "$F".tar
    tar vxzf "$F".tgz
    tar vxjf "$F".tbz

f: from file given as next arg, not stdin

# rar

Proprietary Roshal ARchive.

Can do split archive.

Split archive extensions:

- .part\d+.rar
- .r\d+

extract contents of a.rar to ./

    unrar x a.rar

Before / after:

    a.rar
    /dir1/
    /dir1/f1
    /dir1/f2

    ===============

    a.rar
    dir1/f1
    dir1/f2

out to ./out/, creates this folders if necessary:

    unrar x a.rar out

extract multipart rar

    unrar x a.r00
    unrar x a.part1.rar

recursivelly finds all files in a.rar, and outputs them to current dir
with old basename possible name conflicts

    unrar e a.rar

sample output:

    a.rar
    /dir1/
    /dir1/f1
    /dir1/f2

    ===============

    a.rar
    f1
    f2

# 7zip

Microsoft proprietary program.

Can do lots of formats:

- 7z format
- rar with p7zip-rar installed
- zip

But *use only for 7z*, which it was made for.

With 7zip, you can open .exe files to extract their inner data.

# File roller

Very good gui app to view inside archives and extrac them.