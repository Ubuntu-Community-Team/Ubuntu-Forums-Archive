---
title: "Cause it confused me heres my findings (MP3 tag +mythmusic)"
date: 2010-05-03
forum: Mythbuntu
---

### Post by geekyhawkes on 2010-05-03
I have just been through my 7000mp3s and finally got round to sorting most of the ID3 tags (including album art), imagine my surprise when i then updated my mythmusic library and found lots of the changes were not carried across!

After some digging below are my findings in case anyone else finds themselves in this position;

I updated my MP3 tags with easytag, great program for linux and easy to use although lacking links to CDDB etc.  In the options of Easytag is a fairly easy to miss option that selects to update the file modification time when re-taging, i missed this before the process began!  By default Easy tag does not update the modification time of the files as you go, and mythmusic uses the modification time to work out what has changed (the problem should be clear now!).

If starting over i would just tick this option in easytag and all would be fine in mythmusic.

If you find yourself in the position I was in then the Bash command to help you out is touch.  It can create files but more importantly for us in this case updates modification and accessed times for the files.

Sadly touch doesnt have recursive functionality (ie to enter your sub directories and update the files in them) and as MP3 folders/file names tend to have spaces the solution wasnt that obvious (to me at least).

The solution i ended up with is posted below and ran from the top directory (in my case /nas/MP3s);

sudo find . -exec touch -m {} \;


All seems to be well now, heres hoping this is useful for someone else.

---

