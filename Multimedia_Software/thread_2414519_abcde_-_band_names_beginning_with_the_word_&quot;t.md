---
title: "abcde - band names beginning with the word &quot;the&quot;"
date: 2019-03-11
forum: Multimedia Software
---

### Post by z7APXKm on 2019-03-11
Has anyone found a way of getting abcde to alter the artist name if it begins with the word "The " ?

eg.

"The Cure" becomes "Cure, The"
"the Cure" becomes "Cure, The"
"Therapy" remains unchanged

thanks

---

### Post by robbie 348 on 2019-03-11
It might have problems with "The The", if anyone remembers them. OOH! it might have problems with "Them" as well

---

### Post by z7APXKm on 2019-03-11
Good one!

I think the logic would be something like, 

if the leftmost 4 characters of the artist name is equal to "the " (case insensitive search)
then
set the artistname to be mid(artistname, 4, len(artistname)) +', The'

Just not quite sure how I can do that within the .abcde conf file.

Alternatively, I guess I could rename the folder once ripping has completed.

---

### Post by mc4man on 2019-03-11
On a 18.04 install didn't have abcde setup so installed it, (2.9-2) put a .abcde.conf for flac in (copied from [Andrew.46's site]("http://www.andrews-corner.org/abcde.html"), edited only to use libcdio.
Used the 1st The ...  cd I   found (The Band), works fine..
What abcde.conf are you using?

---

### Post by z7APXKm on 2019-03-12
Mine would do the same:

> # System defaults for abcde version 2.8.1# Nothing in this file is uncommented by default.
#
# If you wish to override these system-wide settings, create your own
# .abcde.conf file in your home directory.


OUTPUTDIR=/home/music/
OUTPUTTYPE=flac
OUTPUTFORMAT='${ARTISTFILE} - ${ALBUMFILE}/${TRACKNUM} - ${TRACKFILE}'
PADTRACKS=y
INTERACTIVE=n
mungefilename ()
{
        echo "$@" | sed -e 's/^\.*//' | tr -d ":><|*/\"'?[:cntrl:]"
}
EJECTCD=y




I'm looking to be able to save the folder as "Band, The - AlbumName"

I could probably figure it out if I knew how mungefilename() worked.  It looks like each variable is passed to it (ARTISTFILE, ALBUMFILE, TRACKFILE) in order to get "cleaned".  If this is correct, how would one put in a routine that only applied to ARTISTFILE?

Or can this logic be added outside of the function?

---

### Post by z7APXKm on 2019-03-12
OK, so this is working in bash, given a variableName of $ARTISTFILE

```
ARTISTFILE="The Fray"
lowerArtist=$(echo "$ARTISTFILE" | tr '[:upper:]' '[:lower:]')
if [[ $lowerArtist == "the "* ]] ;
then
  ARTISTFILE=$(echo $ARTISTFILE | cut -c 4-)', The'
fi

```

Still trying to work out how to get it into the .abcde.conf file

---

### Post by z7APXKm on 2019-03-15
OK, here's what I did...

1.  Take a copy of the .abcde.conf file into the local home directory and edit to add a new mungeartistname2 function:

```

# System defaults for abcde version 2.8.1
# Nothing in this file is uncommented by default.
#
# If you wish to override these system-wide settings, create your own
# .abcde.conf file in your home directory.


OUTPUTDIR=/home/music/
OUTPUTTYPE=flac
OUTPUTFORMAT='${ARTISTFILE} - ${ALBUMFILE}/${TRACKNUM} - ${TRACKFILE}'
PADTRACKS=y
INTERACTIVE=n


mungefilename ()
{
  echo "$@" | sed -e 's/^\.*//' | tr -d ":><|*/\"'?[:cntrl:]"
}


mungeartistname2 ()
{
  if [[ $(echo "$@" | tr '[:upper:]' '[:lower:]') == "the "* ]] ;
  then
    echo "$(mungefilename $@ | cut -c 5-), The"
  else
    echo "$(mungefilename $@)"
  fi
}


EJECTCD=y



```

2.  Edit the abcde main script at /usr/bin/abcde 
We're editing the mungeartistname() function.  Instead of calling the generic mungefilename function, it calls the wrapper function mungeartistname2:

```

   3490 # Custom filename munging specific to artist names:
   3491 mungeartistname ()
   3492 {
   3493         mungeartistname2 $@
   3494 }

```

NOTE:  I'm sure this could be improved upon, and it's also probably not advisable to edit /usr/bin/abcde directly as future updates will overwrite it.  Then again, it's only a one line change and easy to put back if needs be.

---

