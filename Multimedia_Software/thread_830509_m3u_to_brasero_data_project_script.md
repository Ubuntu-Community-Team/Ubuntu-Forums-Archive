---
title: "m3u to brasero data project script"
date: 2008-06-15
forum: Multimedia Software
---

### Post by vladimirprieto on 2008-06-15
hi everybody!

i [was looking]("http://ubuntuforums.org/showthread.php?t=759576") for some way to burn playlist of mine (m3u) as data files **not audio cd** but i couldm't find a way to do it.  so after [some search]("http://linuxgazette.vlsm.org/141/misc/lg/2_cent_tip__summing_up_file_sizes.html") i build this script:

```
#!/bin/bash
# Created by Vladimir Prieto 2008-06-15

# Exit with usage message unless specified file exists and is readable
[ -r "$1" ] || { printf "Usage: ${0##*/} <file.m3u>\n"; exit; }

#defining the burner program
burner="brasero -d "

# For the purposes of the loop, ignore spaces in filenames
old=$IFS
IFS='
'

# Get the files
for n in `cat "$1"`; do
        if [ ${n:0:1} == "/" ]
        then
                files="$files \"$n\" ";
        fi
done

# Restore the IFS
IFS=$old

#output
echo "brasero -d $files"

#calling brasero
$burner $files

```

what it does?

it generates the command for brasero with the files inside the playlist (m3u) ready to be burn **AS DATA NOT AUDIO CD**.

but i have one problem:

the script above works if you copy&paste the output command, but the script tries to execute it and brasero showme some errors on generating the new project.  if you pick up the command and you run it apart (copy&paste) it runs as spected.

don't why happens that if it the same command running.  so, if someone could helpme it would be great.

hope helps someone out there.

cu.

---

### Post by nunacho on 2009-10-28
```

#!/bin/bash

die() {
    echo $@ >&2
    exit 1
}

[ -f "$1" ] || die "Usage: ${0##*/} <file.m3u>"

BURNER="brasero -d"

FILES=()
I=0
while read LINE; do
    if [ ${LINE:0:1} == "/" ]; then
        FILES[$I]=$LINE
        I=$(($I+1))
    fi
done < "$1"

echo $BURNER ${FILES[@]}
$BURNER "${FILES[@]}"

```

---

### Post by epitaph on 2010-06-05
Thank you for this -- just what I was looking for!

---

### Post by Kate454 on 2011-08-03
It helped a lot, I looked for some help too and you research info helped thank you no is just one problem less

---

