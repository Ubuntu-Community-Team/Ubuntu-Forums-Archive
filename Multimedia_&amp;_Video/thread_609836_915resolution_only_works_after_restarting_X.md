---
title: "915resolution only works after restarting X"
date: 2007-11-11
forum: Multimedia &amp; Video
---

### Post by mistachie777 on 2007-11-11
I recently installed Ubuntu (upgraded to Gutsy Gibbon) on an Acer Aspire 5610 laptop.  Like most other Acers, the graphics card is an Intel Mobile 945GM Express.  My resolution was stuck at 1024x768 (supposed to be 1280x800) so I downloaded 915resolution and followed the directions.  I had to override one of the predefined modes by editing /etc/default/915resolution as the tutorials explain to.  However, when I rebooted the resolution went back to 1024x768 and when I ran ```
915resolution -l
``` I found the mode I had overridden had been reset to its default resolution.  In order to restore the proper resolution, I had to run ```
sudo 915resolution 58 1280 800
``` and restart X.

I followed another tutorial in which I added ```
915resolution 58 1280 800
``` to /etc/rc.local.  Now I only have restart X after booting to restore the resolution.  Is there anything I can do so that the resolution is correct upon booting without having to restart X?

---

### Post by scratched on 2007-11-11
In your [FONT="Courier New"]/etc/rc.local[/FONT] file add the following lines:
```
if [ `runlevel | cut -f2 -d' '` -eq 5 ]; then
#runscript
855resolution 7d 1280 800
fi
```

See if that works:)

---

### Post by mistachie777 on 2007-11-11
Should I use ```
915resolution 58 1280 800
``` instead of ```
855resolution 7d 1280 800
``` in the lines that I add to rc.local?  Thanks for the help :)

---

### Post by scratched on 2007-11-11
yeah. Sorry, I copied that code out of an old setup guide from the 855resolution. Just change it to your version. Hopefully that works for you.

---

### Post by mistachie777 on 2007-11-12
Well, it didn't work. I know that the if statement doesn't even get executed because I have to manually run 915resolution after booting and then restart X.  And if I remark out the if statement, then the command runs if I restart X like before.  Do the parameters need to be changed because I'm using 915resolution instead of 855resolution?  Or has there been a syntax change in Ubuntu since that script was written?  Unfortunately, I'm not too familiar with shell scripting in Linux, so I don't know what the statement is actually checking for or how to fix it.  Thanks for the help so far, I'm surprised that this has been such a tough problem to fix!

---

### Post by mistachie777 on 2007-11-19
Sorry to bump this thread, I know this is fairly trivial, but I would still like to know if there is any way I can get 915resolution to run without having to restart X.  If anyone has an idea, please share it!

---

