---
title: "[SOLVED] Ubuntu 6.06 won't play my audio CD's"
date: 2007-04-12
forum: Multimedia &amp; Video
---

### Post by JawsThemeSwimming428 on 2007-04-12
I recently tried to play an audio cd in Ubuntu 6.06 (Dapper) to no avail. When I inserted my CD into the drive (either one I have a Lite-On CD-ROM drive and I have a BTC 16x Beige DVD-ROM) I got the following error message: "Couldn't display "cdda:///dev/hdb".
There was an error launching this application.

So I looked around and I thought it might be my audio application. I found a website that had the launcher for the xmms media player so I inserted the following command into the System->Preferences->Removable Drives and Media dialog, on the Mutlimeda Tab under Audio CD Discs in the Command box:

"xmms -p /media/cdrom"

I don't have the xmms media player nor do I want it (sorry I'm a Linux newcommer). So I am not sure what command I need to have there. The music player I would like to use is Amarok. I do have Amarok installed. So if someone can tell me the code to put there that would be great! But before I even changed that I was getting the same error. Could there be something wrong with the drive mounting? When I put the CD in either drive it loads the icon on the desktop and says "Audio Disc" but when I click it I get that error message. Any help would be much appreciated!!!!!! Thanks in advance.

---

### Post by deadgobby on 2007-04-13
[https://help.ubuntu.com/community/Amarok#head-2fb0409201430e3e0496](https://help.ubuntu.com/community/Amarok#head-2fb0409201430e3e0496)

---

### Post by tommcd on 2007-04-13
Have you installed the multimedia codecs?
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
You need all the gstreamer plugins. Get them from synaptic. Also scroll down to the Audio section for other stuff. Hope this helps.

---

### Post by tommcd on 2007-04-13
Have you installed the multimedia codecs?
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
You need all the gstreamer plugins. Get them from synaptic. Also scroll down to the Audio section for other stuff. Hope this helps.
EDIT: Fiesty will be out soon, and will have a noob friendly way to get all the codecs from what I read. You may want to upgrade from 6.06 when Fiesty comes out.

---

### Post by JawsThemeSwimming428 on 2007-04-13
Thanks for the quick responses everyone! I installed the Restricted Formats. When I insert an audio CD, my CD-ROM drive recognizes it as an audio cd but will not play it. I get the same error message I posted above. Any ideas?

---

### Post by tommcd on 2007-04-13
How is your cdrom drives listed in fstab? Post the output of:
cat /etc/fstab

Couldn't display "cdda:///dev/hdb".
Do you get that error message when you just put the cd in , or when you open a media player? If you have 2 drives one should be /dev/hdb, and the other /dev/hdc, or something like that. What happens if you insert a data cd?  Can you open it and see the contents?
Try putting a cd in and opening rhythmbox and see if you can play it. You may need to set the preferences of your media players to match the fstab listing. But lets see your fstab.

---

### Post by JawsThemeSwimming428 on 2007-04-14
I installed Rhythmbox and Sound Juicer and now I can play the audio files when I rip them to my hard drive with Sound Juicer. I still don't think something is right with my drive configurations. Here is the output of the command:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       none            swap    sw              0       0
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0

---

### Post by tommcd on 2007-04-14
Rhythmbox and soundjuicer should have been installed with the default ubuntu install.
Do you have 2 cdrom drives? Ubuntu only sees 1:

/dev/hdb /media/cdrom0 udf,iso9660 user,noauto 0 0

Your fstab entry looks ok as near as I can tell. When I get home from work I'll compare it to mine.
I don't understand how you can rip the tracks with rhythmbox but you can't play them. Lets start from the beginning.
1) when you put a cd in the drive does a cd icon pop up on the desktop?
2) assuming yes,  does rhythmbox open automatically to play it?
3) assuming yes, or after you manually open rhythmbox, does it list the tracks on the cd?
4) assuming yes, what happens when you click the play button on rhythmbox? Where in the process do you get the errors?

Also check the edit>preferences on rhythmbox, somewhere in there it should tell you what it thinks your cdrom drive is called. It should point to /dev/hdb or /media/cdrom0.

---

### Post by JawsThemeSwimming428 on 2007-04-14
Yes, I have a DVD-ROM and CD-ROM drive and only one is recognized. I am not sure why. No Rhythmbox does not automatically play the audio cd when I put it in. Yes I do get a CD-Drive icon on my desktop. Thanks for you help. I'll be back later.

---

