---
title: "burning from cuefile with wodim  help required!"
date: 2010-12-24
forum: Multimedia Software
---

### Post by shantiq on 2010-12-24
anyone knows how to burn from cuefile with wodim


so far i have failed to work it out and end up with just one track


i cannot understand the syntax in the manual

it says

```
-text  Write CD-Text information based on information taken from a file
              that contains ascii information for  the  text  strings.   wodim
              supports  CD-Text  information based on the content of the *.inf
              files created by icedax and CD-Text  information  based  on  the
              content  from  a  CUE  sheet file.  If a CUE sheet file contains
              both (binary CDTEXTFILE and text based SONGWRITER) entries, then
              the information based on the CDTEXTFILE entry will win.

              You need to use the -useinfo option in addition in order to tell
              wodim to read the *.inf files or cuefile=filename  in  order  to
              tell wodim to read a CUE sheet file in addition.  If you like to
              write your own CD-Text information, edit the *.inf files or  the
              CUE sheet file with a text editor and change the fields that are
              relevant for CD-Text.

       textfile=filename
              Write CD-Text based on information  found  in  the  binary  file
              filename.   This  file must contain information in a data format
              defined in the SCSI-3 MMC-2 standard and in the  Red  Book.  The
              four  byte  size  header that is defined in the SCSI standard is
              optional and allows to make the recognition of correct data less
              ambiguous.   This  is the best option to be used to copy CD-Text
              data from existing CDs that already carry  CD-Text  information.
              To  get  data in a format suitable for this option use wodim -vv
              -toc  to  extract  the  information   from   disk.    If   both,
              textfile=filename  and  CD-Text  information from *.inf or *.cue
              files are present, textfile=filename will  overwrite  the  other
              information.

       cuefile=filename
              Take  all  recording related information from a CDRWIN compliant
              CUE sheet file.  No track files are allowed when this option  is
              present and the option -dao is currently needed in addition.

```


and i have tried   DO NOT USE OF COURSE

```
           wodim dev=/dev/cdrw -v   speed=2 -dao -useinfo -text 1.cue    1.wav
```

where the file is named 1


also                   ```
wodim dev=/dev/cdrw -v   speed=2 -dao -text cuefile=1.cue  1.wav
```


**can someone make sense of this** or has simply done it before       i find those manuals often perplexing


=======================================
=======================================


with cdrdao no problem!!!    but would like to know for wodim as i am sure it is simple once u know

from cue
[SIZE="2"]This you can use
[/SIZE]    ```
**cdrdao write --eject --speed 8 --device /dev/sr0  --driver generic-mmc   name.cue**
```


i pick speed 8 here as it gives a more likely-not-to-skip burn but of course 48 or 52 or 208 :KS:KS (for readers of the future) is available and may be your choice
========

---

### Post by alonc on 2011-05-06
It's been a while but I was looking for the same thing.
Your post was very helpfull for me :)

The documentation you posted here about cuefile says:

“No track files are allowed when this option  is present”

I ommited the wav file name from the commad and burned a CD using this command line:

```

wodim dev=/dev/cdrw -v speed=8 -dao -text cuefile=1.cue

```

and it worked perfectly!

maybe it will help somebody else looking for this.

---

### Post by shantiq on 2011-05-06
thanx alonc makes sense   do not know why i added 1.wav  :D

---

