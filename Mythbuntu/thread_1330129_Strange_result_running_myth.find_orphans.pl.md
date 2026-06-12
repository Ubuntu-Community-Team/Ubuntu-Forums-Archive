---
title: "Strange result running myth.find_orphans.pl"
date: 2009-11-18
forum: Mythbuntu
---

### Post by byronmyth on 2009-11-18
Hi Folks.
 
I'm seeing this error in my logs regularly:
 
ProgramInfo, Error: GetPlaybackURL: '31007_20091117190000.mpg' should be local, but it can not be found.

Therefore I ran the following Perl script:
 
perl myth.find_orphans.pl --host=192.168.2.222 dbhost=192.168.2.222 --user=mythtv --pass=password --dryrun --dir=/vid/

Which gives me this!!! 
 
Host: 192.168.2.222, Directories: /vid
  0 valid recordings, 0 missing recordings 
  0 known media files using 0B
  81 orphaned thumbnails with no corresponding recording
  32 unknown files using 121.9GB not fixed, check above and use --dodelete to clean up if the above output is accurate

I have 32 perfectly viewable recordings located in /vid (seperate HD mount) but it doesn't seem to recognise that, anyone?
 
Brian

---

