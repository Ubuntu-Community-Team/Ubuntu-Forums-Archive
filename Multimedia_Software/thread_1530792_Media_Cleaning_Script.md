---
title: "Media Cleaning Script"
date: 2010-07-14
forum: Multimedia Software
---

### Post by kyleabaker on 2010-07-14
Hey guys/girls,

I'm looking for a way to scan my music collection's meta data to find songs that don't have leading Capitals. Example...I want to change the file:

**eric clapton - its in the way that you use it**
artist: eric clapton; title: its in the way that you us it

to...

**Eric Clapton - Its In The Way That You Use It**

Is there a way that I can query my music to find words that don't start with capitals and change them? Please help!?! Al scripts are welcome!

---

### Post by DaithiF on 2010-07-14
Hi,
Do you want to manipulate the id3 tags embedded in the mp3 files (as opposed to manipulating the file names themselves)?

assuming that is the case, you could do something like this:
```
find Music -name '*.mp3' -exec ./capitalise_meta.sh noexec {} \;

```

where capitalise_meta.sh is this script:

the noexec option will display any tags that it would update but won't actually apply those updates.  If the output looks reasonable then remove the noexec option to actually make the changes

i've no doubt there are cases this won't match particularly well, e.g. "this song's crap" would get capitalised to "This Song'S Crap".  And depending on your music collection there'll probably be other corner cases also.  Either fix those manually after running the script, or else refine the sed regex to do something more sophisticated.

```
#!/bin/bash

if [[ $1 == "noexec" ]]; then
    noexec="1"
    shift
fi

file=$1

[[ ! -f "$file" ]] && { echo "file not found: $file, exiting..."; exit 1;}

meta=$(id3tool "$file")

title=$(echo "$meta" | grep "Song Title:" | cut -d: -f2 | sed 's/^\s*//')
if [[ -n "$title" ]]; then
    capitalised_title=$(echo "$title" | sed 's/\(\w\+\)/\u\1/g')
    if [[ "$capitalised_title" != "$title" ]]; then
        if [[ -z "$noexec" ]]; then
            id3tool -t "$capitalised_title" "$file"
        else
            echo "Noexec: Title: $title => $capitalised_title"
        fi
    fi
fi

artist=$(echo "$meta" | grep "Artist:" | cut -d: -f2 | sed 's/^\s*//')
if [[ -n "$artist" ]]; then
    capitalised_artist=$(echo "$artist" | sed 's/\(\w\+\)/\u\1/g')
    if [[ "$capitalised_artist" != "$artist" ]]; then
        if [[ -z "$noexec" ]]; then
            id3tool -r "$capitalised_artist" "$file"
        else
            echo "Noexec: Artist: $artist => $capitalised_artist"
        fi
    fi
fi

```

good luck

---

