---
title: "How to remove &quot;-g&quot; option from transcode with mythdvd ripper?"
date: 2009-05-03
forum: Mythbuntu
---

### Post by Drostin77 on 2009-05-03
When I import dvds using mythdvd it tells me what the transcode command is:

transcode -x vob -J extsub=track=0 -i /var/lib/mythdvd/temp/Anchorman/vob/ -g 720x480 -M 2 -V -Z 856x480 -y xvid,null -A -N 0x2000 -o /dev/null --print_status 20 --color 0 -R 1,twopass.log
 
I have learned out to force this command to have a specific output resolution (the -Z option shown), but it is still using the "-g 720x480" parameter.  This parameter specifies the input stream, and the input is NOT 720x480, so I would like to remove this "-g 720x480" from the transcode command that importing dvds uses..

---

