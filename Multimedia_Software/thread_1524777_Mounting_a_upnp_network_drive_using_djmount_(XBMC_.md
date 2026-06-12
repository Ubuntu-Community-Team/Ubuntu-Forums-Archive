---
title: "Mounting a upnp network drive using djmount (XBMC Live)"
date: 2010-07-05
forum: Multimedia Software
---

### Post by djrobthaman on 2010-07-05
Hi,

I've done much research on using XBMC with a upnp network drive and have discovered that XBMC can stream the files located on such a drive but does not support scraping for metadata with them.

So, I've decided to implement a workaround whereby I mount the upnp drive as if it were a local drive in the /media folder.

I've done all my homework and the following commands work for me when I am in the command line interface of XBMC Live:

sudo modprobe -l -t /media/Media/ fuse
djmount /media/Media

Once these commands are executed, the /media/Media folder now contains all the contents of my upnp drive.

My problem is that I can't figure out how to run these commands automatically on start up.  I've tried inserting the commands in both the runXBMC file and the rc.local file.  Neither seem to work.

So:

1. How do I get commands like the ones shown above to be run on startup with root privileges?

2. Would I also need to run 'mount -a' after the above commands in order to mount the drive and have it easily discoverable in the "Add Source" dialogue?

3. Am I doing it all wrong and is there some really simple method to scrape from a upnp drive that I have somehow overlooked in my research?

Thanks for the help.

---

