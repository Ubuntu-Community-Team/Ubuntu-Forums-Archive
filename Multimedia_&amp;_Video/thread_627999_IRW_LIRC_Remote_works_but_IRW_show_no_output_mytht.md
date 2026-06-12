---
title: "IRW LIRC Remote works but IRW show no output mythtv"
date: 2007-11-30
forum: Multimedia &amp; Video
---

### Post by sonic6567 on 2007-11-30
hello,

I have 7.10
i installed mythtv and it seems to be working fine

I want to use my snapstream firefly remote

i have followed several procedures and spent two days searching already for the answer with no luck.

lirc is running.

irrecord works correctly and reads input from my remote
mode2 displays data from my remote correctly.

but irw displays nothing and mythtv will not respond to the remote either.

Please help.

Thanks
Ben

---

### Post by MaxWildwood on 2007-12-08
Did you ever get this working?  I have a similar problem with the Firefly RF Remote not working.  In my case, irw runs, but there is no message from the remote.

I installed the remote on another computer running Windows XP and the remote works fine.

I am running Mythbuntu 7.10 and selected Snapstream X10 as the remote.  I checked hardware.conf and other lirc-related files, and they all look OK per the ubuntu lirc instructions.

---

### Post by sonic6567 on 2007-12-09
I did get this working, actually, on my own.  It works great.  But I had no intention of posting the solution as not a single person took a moment to post a reply to my question to try and help out.  But as you are asking now, of course I will be happy to do what I can to help you.

If your irw is working then you are pretty much there.  That means that linux is recognizing your remote just fine and can read information from it. That is a good sign.

My main problem was that I had some bad information in my lircrc and hardware.conf files.  Now, these were the default files that came with mythbuntu so you would expect them to be correct. But no.  I had to edit them to make sure the names of the remotes matched and had no spaces in them.  For example, one file said "Snapstream X10 Remote" and the other file said "Snapstream".  When I edited them to match the names, the thing started working beautifully.

Edit- I re-read your post and think I mis-understood at first.  I thought you meant that irw was running and showing output.  But after re-reading I think your meant it is not showing output.  Anyway, that is even better because it was my exact problem that was fixed by the above.  Also, if you are looking for a shot of confidence or a glimmer of hope that the remote will work for you in linux, try mode2 (i think that was the command).  It showed output even when irw did not.

---

### Post by MaxWildwood on 2007-12-12
I am using the default mythbuntu files, too, so I probably have the same problem with names of the remote.  I'll check them this weekend and let you know what I find out.  Thanks for the tips...

---

### Post by MaxWildwood on 2007-12-12
Well, I went ahead and tried it tonight.  To minimize the amount of text editing, I changed the names in hardware.conf and lircd.conf to Snapstream to match the name in the .lircrc files.  Then I rebooted the machine and ran irw.  This time I finally got a response from the remote!  Now booting up Mythbuntu and the remote is working fine.

In case anyone else wants to know, change the line in hardware.conf from

REMOTE="Snapstream X10 RF"

to 

REMOTE="Snapstream"

and change the line in lircd.conf from

remote Snapstream Firefly

to 

remote Snapstream

Both of these files are found in /etc/lirc/.

I also previously made other changes that are recommended in the Ubuntu Lirc installation instructions, including disabling the serial port from kernel usage (see [http://help.ubuntu.com/community](http://help.ubuntu.com/community) and search for Install Lirc Gutsy for details).  However, I don't know if it was necessary.

Thanks for helping me out, even though no one was there to help you!

---

### Post by ablu on 2007-12-16
I'm in the same boat... trying to get the Snapstream Firefly to work on Mythbuntu 7.10...

I tried the trick that worked for both of you.. (using a consistent name "Snapstream" in both the hardware.conf and lircd.conf files) but that doesn't work for me...

mode2 does work so I am confident that the underlying hardware is working right-- although it only works if I run it with the -d option:

sudo mode2 -d /dev/lirc0

irw just sits there but doesn't show any output when I press buttons on the remote... and the remote doesn't work with mythtv either.

Any ideas?  I feel like I'm very close but maybe missing something simple...

---

### Post by ablu on 2007-12-16
I got it working!  All I did was redo my lircd.conf file using the one from:
[https://help.ubuntu.com/community/Install_Lirc_Feisty?action=AttachFile&do=get&target=lircd.conf.firefly](https://help.ubuntu.com/community/Install_Lirc_Feisty?action=AttachFile&do=get&target=lircd.conf.firefly)
changing the name to Snapstream
I guess the one that I had in place was bad...

---

### Post by sonic6567 on 2008-01-27
Got as close to identifying exactly what my specific problem was and fixed it.

I rebuilt the computer from scratch as a test.
A fresh install of mythbuntu (7.10) with the Snapstream selected as the remote did not work by default.

All I had to do to get this working was edit the /etc/lirc/lircd.conf file

I removed everything other than the section for the Snapstream Firefly
I changed the name of the remote to Snapstream (as spaces are not allowed)

Bingo.  Starting working.

Aparently, there is an error somewhere else in the file maybe?  Don't know.

Hope this helps anyone else who was beating their head against the wall.

---

