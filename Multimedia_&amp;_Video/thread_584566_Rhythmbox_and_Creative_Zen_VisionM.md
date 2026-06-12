---
title: "Rhythmbox and Creative Zen Vision:M"
date: 2007-10-21
forum: Multimedia &amp; Video
---

### Post by fettuohi on 2007-10-21
I got my Creative Zen Vision:M 60 GB player working under gutsy but every time I plug it in Rhythmbox is automatically started (I use Amarok to transfer files and sync with my player) is there a way to shut that off?

Regards

André

---

### Post by fettuohi on 2007-10-24
SOLVED: Just had to go into removable media drives and change rhythmbox to Amarok instead. :)

Regards

André

---

### Post by Boobo-oobo on 2007-10-26
Hello, could you tell me how did you solve the problem?? I have Zen visiom M olso, but mine is 30GB. I conect the player but nothing hapens . . . Do i need to install something??

---

### Post by rowanparker on 2007-10-27
System > Prefs > Removable Media > Multimedia tab > bottom one :)

---

### Post by Gary_inNYC on 2007-10-29
Can you please describe (how) you got the Creative Zen Vision:M working?  

I need information on installation of the device itself, any steps on configuration, & what programs are used to transfer files.  I've been scouring the net for any information and have only come to forums which provide no information other than, "I got it working".  Useless to say the least.

My issue is that when I plug the Zen Vision M 60GB player to a USB port, the player immediately freezes and I end up having to reset the player with a needle.

I am running Ubuntu 7.10 at the moment.  This is the last thing I need working before I can completely eliminate my need to boot to Windows, so any help you can give will be greatly appreciated.

- Gary

---

### Post by Gary_inNYC on 2007-10-30
after some digging around, i found that the player locked because of an outdated firmware.  all things equal, (system, software, etc since i dual boot), i downloaded the latest firmware for the Zen Vision M at 

[http://us.creative.com/support/downloads/](http://us.creative.com/support/downloads/)

from my Windows partition, I installed the firmware update, and whatya know, it doesn't freeze anymore in Ubuntu Gutsy when i plug it into a usb port.  

I used two terminal commands to test that my player was at the very minimum, recognized, and functioning as a detectable usb mtp device in Ubuntu Gutsy.  with the updated player plugged in,  

from terminal, run the following 2 commands: 

lsusb
mtp-detect

if any of those commands are absent, Gutsy is smart enough to recommend what you need to install from synaptic.  for me, i had to install mtp-tools to use the mtp-detect command.  simple enough.  Really, I ran the commands twice, (once with the player plugged in, and once without), so that i can find any new devices detected, and I was only glad to find any new reference to a creative device.

After getting the device itself to run and not crash in Ubuntu, THEN, and only then, would I even consider looking for means to transfer files onto the player.  Now that the player is detected and running, after the firmware update,  I searched for and found that the 2 most prevalent **native** programs for Ubuntu to transfer files were:

i.   **gnomad2** works for file transfers, but folders aren't recognized, and i have a pretty particular folder hierarchy that I'm not about to gear away from.  

ii. ** rhythmbox** with** mtp plugin** works with audio transfers, but i have videos and pictures as well, that rhythmbox wasn't able to handle, let alone transfer to my device.  

Both "solutions" technically work, but only on a very relative level depending on your tolerance for _loss in functionality_.  I want to be able to transfer all types of files that the player is compatible with from one compact program.  

gnomad2 can be obtained through synaptic, and rhythmbox is preinstalled with Gutsy. 

Can anyone confirm if they were able to mount the Creative Zen Vision M 60GB as an external USB drive?  If you have, please provide information on how you did it, and also if you were able to transfer all compatible media onto the player from that mount.  

Are there any other ways of file transfer that should be considered?  

- Gary_inNYC

---

### Post by jadedjay on 2007-11-01
Gary_inNYC

Thanks for your info. Ive been using my Creative Vision M 60G with Amarok for a while now and was considering of changing over the Rhythmbox as I think the interface is a bit easier for non-computer people like my girlfriend.  But alas, still no avi file support.

In regards to your question about transfering files to your player as a simple usb device.
That is after defining on your creative vision how much space you want for a usb disk.
The files that you transfer will no be seen by the Creative vision player software.  
If you imagine that you have set up your player as having a multimedia space and simply a disk space (for any files).

If you want the multimedia part of your Creative Vision player to see the files, to my knowledge, you must transfer them via  MTP.  Which having said that, I dont have a solution for, sorry.

Just thought I would pass on my past experiments of trying to fix the same issue.

---

### Post by linux-loser on 2007-11-02
does anyone know how to get it working on feisty?  i was using gnomad2 all day yesturday and it was working pretty well and now i cant get the damn program to connect to the player at all. gnomad just flashes on the screen and goes away.  

is there a way for me to check if i have it set up right or to test if its even connected?  the commands that are posted here do not work for me.

---

### Post by jadedjay on 2007-11-02
Try this, its for Dapper but its what I originally used to set up on Feisty.
[http://ubuntuforums.org/showthread.php?t=199250](http://ubuntuforums.org/showthread.php?t=199250)

Although I would also suggest upgrading to Gutsy as the Creative Vision player with Gnomad or Amarok simply works.  Cant get any simplier plug and play.   

If only we could copy videos,

If you want a quick check to see why Gnomad is flashing and disappearing, maybe running it from the command prompt in a terminal window will cause it to dump some messages.  Or check the last few messages returned with "dmesg"

---

### Post by linux-loser on 2007-11-03
I tried the how-to but im still stuck with the same problem.  i try to launch gnomad2 from the terminal and i get: " Segmentation fault (core dumped)" i have no idea what that means.  

even if i did upgrade to gutsy i still wouldnt be able to get my videos on there and thats equally as important to me.  

I really dont get this, it worked fine for several hours and then it just stopped working, i didnt restart my computer or anything like. it just stopped.

---

### Post by jadedjay on 2007-11-03
Wow a "Segmentation Fault" is certainly much more than I have experienced using Gnomad2 and MTP.  

I presume that when you followed the "how to" you un-installed all your original MTP and Gnomad2 setup?  Sometimes I find its simplier to remove and re-install than to spend hours debugging.

Is you C.V. player being mounted by Feisty before you run Gnomad2?  
When I use to run Feisty it would mount my player as a Camera device.  As I believe the MTP library  has been integrated with a gphoto library, by the developers.
If I was to guess I would say that your player is simply not being found or being mounted incorrectly.  

Does Gnomad crash when you try to open it without your player connected?  It should open with a blank screen.

I found an old link that I used to just setup Gnomad2 before I moved to Amarok.
Have a look a see if anything helps you there.
[http://ubuntuforums.org/showthread.php?t=199250](http://ubuntuforums.org/showthread.php?t=199250)

In particular, make sure that you are using the same versions of library files, I believe that I had to change the version that way automatically installed by Feisty.
Also make sure that the libmtp rules files are corrently copied over.  So the library knows how to handle your player. 

Also make sure that your firmware on your player is up to date, as the latest release helps solve a problem that occurs when trying to disconnect your player from Ubuntu.

Extra Note: If we are to continue this discussion about Gnomad and Creative Vision Players we probably should start a new thread or add to the one I mentioned above.

---

### Post by x_coderchick_x on 2008-05-18
I just installed hardy and I was trying to get it to recognize my 2gb ZenV under Rhythmbox.  Gary_inNYC, your instructions worked flawlessly, I can now transfer music files to and from my player.

THANK YOU!!!

---

### Post by jaithehulk on 2008-05-31
hey ppl.. If u dont want to lose ur folder heirarchy in Creative ZVM then u can use a program called MTPFS... it mounts the ZVM as a HDD with the full directory structure..
Atleast for me the directory structure was intact but music transfer took loads of time..... but hey its better than nothing 
[http://www.adebenham.com/mtpfs/]("http://www.adebenham.com/mtpfs/")

---

