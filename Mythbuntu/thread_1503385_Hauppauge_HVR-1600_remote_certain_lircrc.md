---
title: "Hauppauge HVR-1600 remote certain lircrc"
date: 2010-06-06
forum: Mythbuntu
---

### Post by patmalcolm91 on 2010-06-06
Hello, I'm setting up my first mythbuntu box and am having some troubles with some of the buttons on my remote. I have a Hauppauge WinTV-HVR-1600 tuner card and the included remote (the gray one, not the black MCE-labeled one). I'm running 10.04 with all the latest updates.

I've managed to use irrecord to map all of the buttons to an identifier, but in the mythtv "edit keys" setup, only certain buttons are detected. Non-working keys include the TV, Videos, Music, Pictures, and Radio buttons, and the colored buttons. here is a copy of the file irrecord generated (~/.mythtv/lircrc):

```
# Please make this file available to others
# by sending it to <lirc@bartelmus.de>
#
# this config file was automatically generated
# using lirc-0.8.6(devinput) on Sun Jun  6 14:57:39 2010
#
# contributed by Patrick Malcolm (patmalcolm91@gmail.com)
#
# brand:                       Hauppauge WinTV-HVR-1600 Gray Remote
# model no. of remote control: 
# devices being controlled by this remote:
#

begin remote

  name  myremote
  bits           16
  eps            30
  aeps          100

  one             0     0
  zero            0     0
  pre_data_bits   16
  pre_data       0x8001
  gap          35991
  toggle_bit_mask 0x0

      begin codes
          KEY_RED                  0x018E
          KEY_GREEN                0x018F
          KEY_YELLOW               0x0190
          KEY_BLUE                 0x0191
          KEY_1                    0x0002
          KEY_2                    0x0003
          KEY_3                    0x0004
          KEY_4                    0x0005
          KEY_5                    0x0006
          KEY_6                    0x0007
          KEY_7                    0x0008
          KEY_8                    0x0009
          KEY_9                    0x000A
          KEY_0                    0x000B
          KEY_SUBTITLE             0x0172
          KEY_PLAY                 0x00CF
          KEY_STOP                 0x0080
          KEY_RECORD               0x00A7
          KEY_FASTFORWARD          0x00D0
          KEY_FORWARD              0x00A3
          KEY_REWIND               0x00A8
          KEY_BACK                 0x00A5
          KEY_VOLUMEUP             0x0073
          KEY_VOLUMEDOWN           0x0072
          KEY_ESC                  0x00AE
          KEY_LEFT                 0x0069
          KEY_RIGHT                0x006A
          KEY_UP                   0x0067
          KEY_DOWN                 0x006C
          KEY_ENTER                0x001C
          KEY_MENU                 0x008B
          KEY_MUTE                 0x0071
          KEY_TV                   0x0179
          KEY_VIDEO                0x0189
          KEY_TEXT                 0x0184
          KEY_INFO                 0x008B
          KEY_MENU                 0x016D
          KEY_AUDIO                0x0188
          KEY_RADIO                0x0181
          KEY_PREVIOUS             0x019C
          KEY_POWER                0x0074
          KEY_HOME                 0x0161
          KEY_PROG1                0x016F  # Pictures button
      end codes

end remote

```

In the mythbuntu control center, the remote type is set to "Hauppauge TV Card".

Is there something I'm missing to get mythtv to recognize these buttons? Or should I just map the signals to other keys that do work? If I do have to map them to other keys, what would you recommend?

EDIT: the name of the remote is the A415-HPG. I found some information saying that the buttons I'm having trouble with weren't supported yet, but since irrecord detects the pulses, shouldn't I be able to just map them to keyboard keys? I've not had much luck in my searches, so can someone point me to somewhere I can find the proper configuration for this remote or the status of the work going into supporting these buttons?

---

### Post by TwiztedMatt1007 on 2010-06-06
How in the world did you get the remote to work at all? I seem to be too noobish to even get a single button to work on my 1600. I also have the grey remote.

---

### Post by patmalcolm91 on 2010-06-06
I had to dig through a lot of forums and tutorials, and eventually figured out that I had to enable the kernel module ir-kbd-i2c. That got me basic functionality (also be sure the cable is fully plugged in, as it can be difficult to fully insert because of the location of the port). That provides very basic support (arrow buttons and ok button). Using irrecord to get the posted lircrc file got a few more buttons to function, and that's where i'm at now.

---

### Post by patmalcolm91 on 2010-06-10
Here's some additional info after more searching and troubleshooting:

irw only responds to the number keys, the arrow keys, and the ok button, and the arrow keys show the escape characters (which as i read somewhere might mean that the kernel is catching these events, not lircd) Doing a "cat /dev/input/event5" shows that all the buttons are sending signals (random characters show up onscreen with every press). Changing config files seems to have absolutely no effect on anything, it's always the same few buttons that work. unchecking "Enable a Remote Control" in MCC doesn't stop the buttons from working. Any ideas?

---

### Post by rafe101 on 2010-06-12
Yes, I need help with this too. I just upgraded to 10.04 and am having trouble with the remote. Only the arrow buttons, enter, and power seem to work. 

I did also notice that they were the only ones caught by irw and the remote now navigates other programs and system menus that I hadn't had it set up to do before.

---

### Post by acurarrd1 on 2010-06-24
If anyones still interested, [http://rtr.ca/hvr1600/](http://rtr.ca/hvr1600/), worked for me in lucid. I did have to remap some keys. No biggie. Now all the keys are working. After installing, I just ran irw from a terminal to see what the remote key presses were registering as. Hopefully this will help someone because I know I was ready to poke my own eyeballs out looking for a solution for this.

---

### Post by mycatsnameisbernie on 2010-07-02
I just got this card after reading reviews it worked out-of-the-box with Linux. I guess that review referred to the TV tuner function, not the IR remote.

Thanks to the info in this thread I now have the receiver working. Is there any hope for the IR blaster ever working? Or do I need to get another blaster?

Thanks for the help!

---

### Post by rafe101 on 2010-07-02
I'll have to back out of this discussion. I gave up on lirc and embraced the kernel support. Most of the buttons work now, but there's still a few I can't identify and remap.

---

### Post by mycatsnameisbernie on 2010-07-04
> **mycatsnameisbernie said:**
> Is there any hope for the IR blaster ever working?
 
After much trial, error, Googling, and posting on mythtv-users, I finally have my HVR-1600 IR receiver and blaster both working in Lucid 10.04, with all of the grey Hauppauge remote's keys detected. The key to the solution is to use module lirc_zilog, but it's not easy. Here is how I did it:
 

[LIST=1]
[*]There is lots of old info online pointing at _[lirc_pvr150]("http://www.blushingpenguin.com/mark/blog/?p=24")_. Unfortunately that code is very old and won't build on recent kernels. That modle has been superseded by lirc_zilog.
[*]The best description of lirc_zilog is found on _[Jarod Wilson's blog]("http://wilsonet.com/?p=40")_. His blog refers to the Hauppauge HD-PVR, but most of it applies to the HVR-1600.
[*]Jarod's lirc_zilog code is written for Fedora, and it won't build on Ubuntu without modification. So don't bother trying to download the lirc_zilog code from Jarod's blog. The easiest way to get source code for a Ubuntu-compatible lirc_zilog is to download and use the zilog.diff patch described in _[this post]("http://ubuntuforums.org/showpost.php?p=9211073&postcount=64")_.
[*]Follow the instructions in Jarod's blog to copy the firmware and lircd.conf files from Mark Weaver's site to your system.
[*]Modify /etc/lirc/hardware.conf as follows:
```
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_zilog"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""
#Chosen IR Transmitter
#TRANSMITTER="Command IR : Motorola Cable box"
#TRANSMITTER_MODULES="lirc_dev lirc_serial"
#TRANSMITTER_DRIVER=""
#TRANSMITTER_DEVICE="/dev/lirc1"
#TRANSMITTER_SOCKET=""
#TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
#TRANSMITTER_LIRCD_ARGS=""
```Note that the Transmitter section of hardware.conf is commented out. That is because the single lircd daemon spawned by the REMOTE section handles both receive and transmit.
[*]At this point I thought i was done. But when I rebooted or restarted lircd, my syslog was filled with hundreds of messages of the form
```
Jul  3 09:03:04  mythtv lircd-0.8.6[1110]: error in configfile line 62: 
Jul  3  09:03:04 mythtv lircd-0.8.6[1110]: "2147549184" is out of range
```This is caused by the values in Mark Weaver's lircd.conf being greater than 2**31, but lircd code uses signed 32 bit integers. The fix is to get the source for lircd, change the type of lirc_t to [FONT=Courier New]unsigned int[/FONT], and rebuild and resinstall it, as described in [_this thread_]("http://www.gossamer-threads.com/lists/mythtv/users/441961#441961"). Additional build instructions for lircd can be found [_here_]("http://ubuntuforums.org/showthread.php?t=765454").
[*]Unfortunately, lircd 0.8.6 gets a compile error when building on Lucid. I fixed it by applying _[bug296739a.patch]("http://bugs.gentoo.org/attachment.cgi?id=215141")_ from [_here_]("http://bugs.gentoo.org/show_bug.cgi?id=296739").
[*]My final problem was caused by the default location of lircd in the source code's configure script. It defaults to /usr/local/sbin, but the executable used by Unbuntu is in /usr/sbin. Either run configure with the correct parameters, or copy the lircd executable manually to /usr/sbin.
[/LIST]Now, when you reboot, the irw command should display keys pressed on the remote, and running Mark Weaver's [FONT=Courier New]send_power_new[/FONT] script should cause the visible LED in your blaster to blink. If it doesn't work, check your dmesg, /var/log/syslog, and /var/log/lircd for clues.
 
I have an intermittent problem where lircd sometimes crashes during boot-up. If this happens you will see the following in /var/log/lircd:```
Jul  4 09:32:04 mythtv lircd: caught signal
Jul  4 09:32:04 mythtv lircd: lircd(default) ready, using /var/run/lirc/lircd
```Even though it says it is ready, lircd is non-functional after catching the signal. If that happens, you can recover by restarting it manually with [FONT=Courier New]sudo /etc/init.d/lirc restart[/FONT].
 
You will need to modify Mark Weaver's [FONT=Courier New]change_channel[/FONT] script to refer to the raw codes from the proper code set for your device. I made these changes to do that:```
--- change_channel    2010-07-02 10:31:14.592215719 -0700
+++ change_channel    2010-07-04 15:35:37.192103808 -0700
@@ -12,6 +12,9 @@
 # Change this to point to your rc executable
 $rc_command = "/usr/local/bin/irsend";
 
+# Change this to the prefix for cable box's code set
+$prefix = "0_84_KEY_";
+
 # This subroutine actually sends the signal to the cable box
 sub change_SIGNAL {
     my($SIGNAL) = @_;
@@ -35,7 +38,7 @@
 
     while( $counter < $length )
     {
-    $temp .= substr($SIGNAL,$counter,1) ." ";
+    $temp .= $prefix.substr($SIGNAL,$counter,1) ." ";
     $counter++;
     }
```Change the value of [FONT=Courier New]$prefix[/FONT] to the correct code set for your remote.
 
Thanks to Jarod for creating the driver, and for the help he gave me on the mythtv-users mailing list.
 
Hope that helps...

---

### Post by medley_44 on 2010-07-31
> **acurarrd1 said:**
> If anyones still interested, [http://rtr.ca/hvr1600/](http://rtr.ca/hvr1600/), worked for me in lucid. I did have to remap some keys. No biggie. Now all the keys are working. After installing, I just ran irw from a terminal to see what the remote key presses were registering as. Hopefully this will help someone because I know I was ready to poke my own eyeballs out looking for a solution for this.

Just to elaborate on acurarrd1's suggestion (which also worked for me):

Here's the procedure I followed:

1) Add ir-kbd-i2c to /etc/modules and reboot. (Or run 'modprobe ir-kbd-i2c' to temporarily load the required kernel module). Then you can see if your IR transmitter is detected:

```

$ dmesg | grep " IR "
[   21.977317] tveeprom 0-0050: has no radio, has IR receiver, has IR transmitter
[   22.431856] input: i2c IR (CX23418 Z8F0811 Hauppau as /devices/virtual/input/input4
[   22.433537] ir-kbd-i2c: i2c IR (CX23418 Z8F0811 Hauppau detected at i2c-0/0-0071/ir0 [cx18 i2c driver #0-0]

```

2) Download [http://rtr.ca/hvr1600/fix_hauppauge_remote.tar.gz](http://rtr.ca/hvr1600/fix_hauppauge_remote.tar.gz)
3) Extract and copy the files enable_hauppauge_remote.sh and hauppauge_remote.conf to /usr/local/bin. Note that you do not need to run the included Makefile in Lucid.
4) Next, run 'sudo /usr/local/bin/enable_hauppauge_remote.sh' (which prints a list of key mappings to stdout)

```

$ sudo /usr/local/bin/enable_hauppauge_remote.sh
/dev/input/event4
map: 48 keys, size: 128/128
set: 0x003d =  60  # KEY_F2
set: 0x003b =  61  # KEY_F3
set: 0x0001 =   2  # KEY_1
...

```

You can then open a text editor such as mousepad and press, e.g., the numbered buttons on your Hauppauge remote (while pointing it at the IR receiver, of course). If you see some digits appear in the text editor, you are in business.

It is also important to verify that the IR cable is plugged in all the way! Mine wasn't at first and it led to some frustration as I couldn't understand why the darn thing wouldn't work.

---

### Post by rymonroe on 2010-08-01
> **mycatsnameisbernie said:**
> After much trial, error, Googling, and posting on mythtv-users, I finally have my HVR-1600 IR receiver and blaster both working in Lucid 10.04, with all of the grey Hauppauge remote's keys detected. The key to the solution is to use module lirc_zilog, but it's not easy. Here is how I did it:
 

[LIST=1]
[*]There is lots of old info online pointing at _[lirc_pvr150]("http://www.blushingpenguin.com/mark/blog/?p=24")_. Unfortunately that code is very old and won't build on recent kernels. That modle has been superseded by lirc_zilog.
[*]The best description of lirc_zilog is found on _[Jarod Wilson's blog]("http://wilsonet.com/?p=40")_. His blog refers to the Hauppauge HD-PVR, but most of it applies to the HVR-1600.
[*]Jarod's lirc_zilog code is written for Fedora, and it won't build on Ubuntu without modification. The easiest way to build it on Ubuntu, is to use the zilog.diff patch described in _[this post]("http://ubuntuforums.org/showpost.php?p=9211073&postcount=64")_.
[*]Follow the instructions in Jarod's blog to copy the firmware and lircd.conf files from Mark Weaver's site to your system.
[*]Modify /etc/lirc/hardware.conf as follows:
```
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_zilog"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""
#Chosen IR Transmitter
#TRANSMITTER="Command IR : Motorola Cable box"
#TRANSMITTER_MODULES="lirc_dev lirc_serial"
#TRANSMITTER_DRIVER=""
#TRANSMITTER_DEVICE="/dev/lirc1"
#TRANSMITTER_SOCKET=""
#TRANSMITTER_LIRCD_CONF="motorola/dctxxxx.conf"
#TRANSMITTER_LIRCD_ARGS=""
```Note that the Transmitter section of hardware.conf is commented out. That is because the single lircd daemon spawned by the REMOTE section handles both receive and transmit.
[*]At this point I thought i was done. But when I rebooted or restarted lircd, my syslog was filled with hundreds of messages of the form
```
Jul  3 09:03:04  mythtv lircd-0.8.6[1110]: error in configfile line 62: 
Jul  3  09:03:04 mythtv lircd-0.8.6[1110]: "2147549184" is out of range
```This is caused by the values in Mark Weaver's lircd.conf being greater than 2**31, but lircd code uses signed 32 bit integers. The fix is to get the source for lircd, change the type of lirc_t to [FONT=Courier New]unsigned int[/FONT], and rebuild and resinstall it, as described in [_this thread_]("http://www.gossamer-threads.com/lists/mythtv/users/441961#441961"). Additional build instructions for lircd can be found [_here_]("http://ubuntuforums.org/showthread.php?t=765454").
[*]Unfortunately, lircd 0.8.6 gets a compile error when building on Lucid. I fixed it by applying _[bug296739a.patch]("http://bugs.gentoo.org/attachment.cgi?id=215141")_ from [_here_]("http://bugs.gentoo.org/show_bug.cgi?id=296739").
[*]My final problem was caused by the default location of lircd in the source code's configure script. It defaults to /usr/local/sbin, but the executable used by Unbuntu is in /usr/sbin. Either run configure with the correct parameters, or copy the lircd executable manually to /usr/sbin.
[/LIST]
Now, when you reboot, the irw command should display keys pressed on the remote, and running Mark Weaver's [FONT=Courier New]send_power_new[/FONT] script should cause the visible LED in your blaster to blink. If it doesn't work, check your dmesg, /var/log/syslog, and /var/log/lircd for clues.
 
I have an intermittent problem where lircd sometimes crashes during boot-up. If this happens you will see the following in /var/log/lircd:```
Jul  4 09:32:04 mythtv lircd: caught signal
Jul  4 09:32:04 mythtv lircd: lircd(default) ready, using /var/run/lirc/lircd
```Even though it says it is ready, lircd is non-functional after catching the signal. If that happens, you can recover by restarting it manually with [FONT=Courier New]sudo /etc/init.d/lirc restart[/FONT].
 
You will need to modify Mark Weaver's [FONT=Courier New]change_channel[/FONT] script to refer to the raw codes from the proper code set for your device. I made these changes to do that:```
--- change_channel    2010-07-02 10:31:14.592215719 -0700
+++ change_channel    2010-07-04 15:35:37.192103808 -0700
@@ -12,6 +12,9 @@
 # Change this to point to your rc executable
 $rc_command = "/usr/local/bin/irsend";
 
+# Change this to the prefix for cable box's code set
+$prefix = "0_84_KEY_";
+
 # This subroutine actually sends the signal to the cable box
 sub change_SIGNAL {
     my($SIGNAL) = @_;
@@ -35,7 +38,7 @@
 
     while( $counter < $length )
     {
-    $temp .= substr($SIGNAL,$counter,1) ." ";
+    $temp .= $prefix.substr($SIGNAL,$counter,1) ." ";
     $counter++;
     }
```Change the value of [FONT=Courier New]$prefix[/FONT] to the correct code set for your remote.
 
Thanks to Jarod for creating the driver, and for the help he gave me on the mythtv-users mailing list.
 
Hope that helps...


Ok, I have a hvr-1600 and am trying to get the Remote and blaster working. Thank you for all your help but I am still having trouble with it. When I go to Jarods Blog and try to download the lirc_zilog I am unsuccessful (it says 404 - no such tree and keeps on refreshing the page). I was wondering if you could tell me if I am supposed to download lirc_zilog from Jarods Blog or if I'm doing something wrong. Just so I'm reading the first part of your instructions correctly...

First, download lirc_zilog off of Jarod Wilsons blog. 

Second, use "this post" ([http://ubuntuforums.org/showpost.php?p=9211073&postcount=64](http://ubuntuforums.org/showpost.php?p=9211073&postcount=64)) to build the lirc_zilog. 

Third, Follow Mark Weaver's site to get the firmware and lircd.conf files .

Fourth, modifiy /etc/lirc/hardware.conf...

If I am reading this incorrectly, I would appreciate it if you would let me know. Thank you very much for your help.

---

### Post by medley_44 on 2010-08-01
> **acurarrd1 said:**
> If anyones still interested, [http://rtr.ca/hvr1600/](http://rtr.ca/hvr1600/), worked for me in lucid. I did have to remap some keys. No biggie. Now all the keys are working. After installing, I just ran irw from a terminal to see what the remote key presses were registering as. Hopefully this will help someone because I know I was ready to poke my own eyeballs out looking for a solution for this.

acurarrd1,

When you say you remapped some keys, did you mean in MythTV or in the hauppauge_remote.conf file? I'm noticing that some of the buttons on the remote do nothing (e.g., the TV and Music buttons), and some buttons appear to be mapped to the same keys.

If you modified your hauppauge_remote.conf, could you please post it? Thanks.

---

### Post by mycatsnameisbernie on 2010-08-03
I guess my instructions weren't clear. Don't download the lirc_zilog source code from Jarod Wilson's blog" The file you are having trouble downloading is for Fedora and won't build on Ubuntu. 
 
The zilog.diff file in "[this post]("http://ubuntuforums.org/showpost.php?p=9211073&postcount=64")" includes the Ubuntu download for lirc_zilog.
 
Hope that helps...
 
 
> **rymonroe said:**
> Ok, I have a hvr-1600 and am trying to get the Remote and blaster working. Thank you for all your help but I am still having trouble with it. When I go to Jarods Blog and try to download the lirc_zilog I am unsuccessful (it says 404 - no such tree and keeps on refreshing the page). I was wondering if you could tell me if I am supposed to download lirc_zilog from Jarods Blog or if I'm doing something wrong. Just so I'm reading the first part of your instructions correctly...
 
First, download lirc_zilog off of Jarod Wilsons blog. 
 
Second, use "this post" ([http://ubuntuforums.org/showpost.php?p=9211073&postcount=64](http://ubuntuforums.org/showpost.php?p=9211073&postcount=64)) to build the lirc_zilog. 
 
Third, Follow Mark Weaver's site to get the firmware and lircd.conf files .
 
Fourth, modifiy /etc/lirc/hardware.conf...
 
If I am reading this incorrectly, I would appreciate it if you would let me know. Thank you very much for your help.

---

### Post by rymonroe on 2010-08-03
Thank you for you patience mycatsnameisbernie. This is the first time I have done anything with Mythtv. I downloaded the zilogg.diff from "this post" by clicking on the link near the top of the page. I was not sure where to save it so I just put it in my home directory. I think this might be where I went wrong but I kept on going anyway. I then folllowed the instructions on "this post" and it worked out well until I typed in the third command and got the error displayed at the bottem of the page. The next command worked well so I just kept following Jarod's instructions. I got to the part where it said "start up lircd" but I do not know how to do that. It then said I could run irw and try key presses but when I do it nothing happens when I push buttons on my remote. If you could point out the mistakes I am making I would be forever grateful. Thank you.


sudo patch -p0 < ~/zilog.diff
patching file lirc-modules-source.conf
Hunk #1 FAILED at 2.
1 out of 1 hunk FAILED -- saving rejects to file lirc-modules-source.conf.rej
patching file dkms.conf
Hunk #1 FAILED at 67.
1 out of 1 hunk FAILED -- saving rejects to file dkms.conf.rej
patching file Makefile
Hunk #1 FAILED at 28.
Hunk #2 FAILED at 124.
2 out of 2 hunks FAILED -- saving rejects to file Makefile.rej
patching file drivers/lirc_zilog/.deps/lirc_zilog.Po
patching file drivers/lirc_zilog/Makefile
patching file drivers/lirc_zilog/lirc_zilog.c
patching file drivers/Makefile
Hunk #1 FAILED at 136.
1 out of 1 hunk FAILED -- saving rejects to file drivers/Makefile.rej

---

### Post by mycatsnameisbernie on 2010-08-03
I had the same problem when I tried the patch the first time. The problem is caused by the patch file being URL-encoded, i.e. quote marks get changed to &quot;
 
The easiest way to fix it is to left-click on the zilog.diff file link in your browser, which will display the patch file. DONT SAVE THE FILE. Instead, copy and paste it into a text editor, and save the file from your text editor. Then run the patch command. It should run with no errors generated. If you can't get the patch to apply properly, don't go any further.
 
> **rymonroe said:**
> sudo patch -p0 < ~/zilog.diff
patching file lirc-modules-source.conf
Hunk #1 FAILED at 2.
1 out of 1 hunk FAILED -- saving rejects to file lirc-modules-source.conf.rej
patching file dkms.conf
Hunk #1 FAILED at 67.
1 out of 1 hunk FAILED -- saving rejects to file dkms.conf.rej
patching file Makefile
Hunk #1 FAILED at 28.
Hunk #2 FAILED at 124.
2 out of 2 hunks FAILED -- saving rejects to file Makefile.rej
patching file drivers/lirc_zilog/.deps/lirc_zilog.Po
patching file drivers/lirc_zilog/Makefile
patching file drivers/lirc_zilog/lirc_zilog.c
patching file drivers/Makefile
Hunk #1 FAILED at 136.
1 out of 1 hunk FAILED -- saving rejects to file drivers/Makefile.rej

---

### Post by rymonroe on 2010-08-05
I was able to run the command correctly and without any errors. Before I did I did type sudo apt-get install lirc. I hope I was supposed to do that. I then followed Jarods Blogs instructions until he says [SIZE=3]_**start up lirc**_[/SIZE]. I'm not sure how to do this. I googled around and think you type lircd but when I type that it says "
ircd: can't open or create /var/run/lirc/lircd.pid
lircd: No such file or directory
"
when I run irw it says "onnect: No such file or directory"

any help would be appreciated.

---

### Post by rymonroe on 2010-08-06
I forgot to mention that before I did all that stuff I reinstalled lucid and started fresh.

---

### Post by p.elsie on 2010-08-06
rymonroe, 

check that /etc/lirc/hardware.conf contains the following:

#Enable lircd
START_LIRCD="true"

Then run:

sudo /etc/init.d/lirc restart

Then run:

grep  lirc /var/log/daemon.log

I am expecting the last two lines to look like this:

lircd-0.8.6[9870]: caught signal
lircd-0.8.6[9994]: lircd(default) ready, using /var/run/lirc/lircd

Hopefully that helps.  

As for myself, I haven't gone so far as to recompile lirc with unsigned int, I was hoping to get 'irw' to read my remote using the file at /usr/share/lirc/remotes/hauppauge/lircd.conf.hauppauge

That's my stumbling block right now.  I am using the HD-PVR 1212 and I was hoping to get past that before I go to the trouble of compiling lirc and trying to get the blaster working.  

I also have a PVR-150, but that's in my production machine and I don't want to mess with it.  

Anyone have a suggestion?  I'm tempted to look for a better supported blaster.  I'll take suggestions there too...

---

### Post by mycatsnameisbernie on 2010-08-06
> **rymonroe said:**
> I was able to run the command correctly and without any errors. Before I did I did type sudo apt-get install lirc. I hope I was supposed to do that. I then followed Jarods Blogs instructions until he says [SIZE=3]_**start up lirc**_[/SIZE]. I'm not sure how to do this. I googled around and think you type lircd but when I type that it says "
ircd: can't open or create /var/run/lirc/lircd.pid
lircd: No such file or directory
"
when I run irw it says "connect: No such file or directory"
 
any help would be appreciated.
[COLOR=#1f497d][COLOR=#1f497d][COLOR=#1f497d][FONT=Calibri][FONT=Verdana][SIZE=2]When you reinstalled Lucid, did you also reinstall mythtv (or mythbuntu)? That should install lirc, and lots of other needed stuff like V4L-DVB. You shouldn’t need to install lirc separately.[/SIZE][/FONT][/FONT][/COLOR]
 
[COLOR=#1f497d][FONT=Calibri][FONT=Verdana][SIZE=2]This is the correct command to (re)start lirc:[/SIZE][/FONT][/FONT][/COLOR][/COLOR][/COLOR][COLOR=#1f497d][FONT=Calibri]```
[COLOR=#1f497d][FONT=Calibri]sudo /etc/init.d/lirc restart[/FONT][/COLOR]
```[/FONT][/COLOR]
 
[COLOR=#1f497d][COLOR=#1f497d][SIZE=2]Your “can’t open or create pid” error most likely means that either lircd was already running when you tried to restart it, or you didn’t use “sudo”.[/SIZE][/COLOR]
 
[SIZE=2][COLOR=#1f497d]Your connect error indicates that lircd did not start correctly, and/or one or more of your config files is incorrect. Did you copy over the firmware and lircd.conf files from Mark Weaver’s site? Did you reapply zilog.patch and dpkg-reconfigure lirc-modules-source? Did you re-edit hardware.conf per step 5 of my instructions?[/COLOR][/SIZE]
[/COLOR]
[SIZE=2][COLOR=#1f497d]To debug this, do the following:[/COLOR][/SIZE]```

[COLOR=#1f497d][SIZE=2][COLOR=#1f497d]sudo /etc/init.d/lirc stop [/COLOR][/SIZE]
[SIZE=2][COLOR=#1f497d]tail -f /var/log/syslog[/COLOR][/SIZE]
[SIZE=2][COLOR=#1f497d]sudo /etc/init.d/lirc start[/COLOR][/SIZE]
[/COLOR]
```[SIZE=2][COLOR=#1f497d]That should cause a bunch of stuff to be logged, which should give you some clues as to what is going on.[/COLOR][/SIZE]
 
[SIZE=2][COLOR=#1f497d]If lirc_zilog is working, you should see log messages like:[/COLOR][/SIZE]```

[COLOR=#1f497d][SIZE=2][COLOR=#1f497d]kernel: [ 318.943013] lirc_zilog: Zilog/Hauppauge IR blaster firmware version 2.1.0 loaded[/COLOR][/SIZE]
 
[SIZE=2][COLOR=#1f497d]and[/COLOR][/SIZE]
 
[SIZE=2][COLOR=#1f497d]lircd-0.8.6[1956]: lircd(default) ready, using /var/run/lirc/lircd [/COLOR][/SIZE]
[/COLOR]
```[SIZE=2][COLOR=#1f497d]Hope that helps…[/COLOR][/SIZE]

---

### Post by rymonroe on 2010-08-06
I use sudo apt-get install mythtv to install mythtv. Should I install it a different way? Either way I am going to uninstall and then reinstall Ubuntu and try this over again from scratch. I will let you guys know how it turns out. Thanks for your help.

Mycatsnameisbernie, I was looking ahead in you instructions and was wondering when you are trying to re-compile lirc and use the patch (_[bug296739a.patch]("http://bugs.gentoo.org/attachment.cgi?id=215141")),  _can you just go to the line # specified and change the code or do you need to download the patch and do something else with it. Thanks.

---

### Post by mycatsnameisbernie on 2010-08-06
> **rymonroe said:**
> I use sudo apt-get install mythtv to install mythtv. Should I install it a different way? 
Your installation method is correct. Your install of mythtv will also install lirc, so you don't need to install lirc separately.
> **rymonroe said:**
> Mycatsnameisbernie, I was looking ahead in you instructions and was wondering when you are trying to re-compile lirc and use the patch (_[bug296739a.patch]("http://bugs.gentoo.org/attachment.cgi?id=215141")), _can you just go to the line # specified and change the code or do you need to download the patch and do something else with it. Thanks.
You can either download the patch and use the patch command to apply it, or else hand-edit the file. It's up to you...

---

### Post by rymonroe on 2010-08-07
I have re-installed Ubuntu and Mythtv. When I type in lircd it says[B] "The program 'lircd' is currently not installed.  You can install it by typing:
sudo apt-get install lirc"[/B] 

I get a similar message if I type irw "[B]The program 'irw' is currently not installed.  You can install it by typing:
sudo apt-get install lirc
"

[/B]When I do a search for files called lirc on my system, I get a bunch files called lirc or similar in[B] /lib/modules/2.6.32-24-generic/kernel/ubuntu/[name of directory with lirc in it]

[/B]I have already set up my backedn. Is my computer not installing mythtv correctly? should I just type sudo apt-get install lirc?

---

### Post by mycatsnameisbernie on 2010-08-07
> **rymonroe said:**
> I have re-installed Ubuntu and Mythtv. When I type in lircd it says** "The program 'lircd' is currently not installed. You can install it by typing:**
**sudo apt-get install lirc"** 
 
I get a similar message if I type irw "**The program 'irw' is currently not installed. You can install it by typing:**
**sudo apt-get install lirc**
**"**
 
When I do a search for files called lirc on my system, I get a bunch files called lirc or similar in** /lib/modules/2.6.32-24-generic/kernel/ubuntu/[name of directory with lirc in it]**
 
I have already set up my backedn. Is my computer not installing mythtv correctly? should I just type sudo apt-get install lirc?
 
I am not an expert: I have only installed mythtv once. I did it the same as you: I installed Ubuntu 10.04 followed by "sudo apt-get install mythtv". But when I installed it, it prompted me for a whole bunch of stuff, including whether or not I was using a remote, and it installed lircd for me.
 
If it's not on your system, go ahead and install lirc yourself.
 
Or instead, you might want to try installing from the Mythbuntu Live CD.

---

### Post by rymonroe on 2010-08-07
I think i'm almost their. I manually installed lirc and followed the instructions by mycatsnameisbernie on page 1. When I try to re-compile lirc as per step 7, I get an error. This is what happens.
```

ryan@DVR-Server:/usr/src/lirc-0.8.6$ sudo /etc/init.d/lirc stop
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
ryan@DVR-Server:/usr/src/lirc-0.8.6$ sudo make
make -C drivers SUBDIRS="lirc_dev"
make[1]: Entering directory `/usr/src/lirc-0.8.6/drivers'
Making all in lirc_dev
make[2]: Entering directory `/usr/src/lirc-0.8.6/drivers/lirc_dev'
Makefile:8: **************************************************
Makefile:8: *** Makefile trick not undone, trying to recover *
Makefile:8: **************************************************
mv Makefile.automake Makefile
make all
make[3]: Entering directory `/usr/src/lirc-0.8.6/drivers/lirc_dev'
cp ./../lirc_dev/Module*.symvers .
cp: cannot stat `./../lirc_dev/Module*.symvers': No such file or directory
make[3]: [lirc_dev.o] Error 1 (ignored)
mv Makefile Makefile.automake
cp ./../Makefile.kernel Makefile
CPPFLAGS="" CFLAGS="" LDFLAGS="" \
    make -C /lib/modules/linux-2.6.32-24-generic/build SUBDIRS=/usr/src/lirc-0.8.6/drivers/lirc_dev modules \
        KBUILD_VERBOSE=1
make: Entering an unknown directory
make: *** /lib/modules/linux-2.6.32-24-generic/build: No such file or directory.  Stop.
make: Leaving an unknown directory
make[3]: *** [lirc_dev.o] Error 2
make[3]: Leaving directory `/usr/src/lirc-0.8.6/drivers/lirc_dev'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/usr/src/lirc-0.8.6/drivers/lirc_dev'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/usr/src/lirc-0.8.6/drivers'
make: *** [dev] Error 2



```In case this helps when I type ```
[COLOR=#1f497d]
[SIZE=2][COLOR=#1f497d]tail -f /var/log/syslog[/COLOR][/SIZE]


[/COLOR]
```[B]ryan@DVR-Server:/usr/src/lirc-0.8.6$ sudo /etc/init.d/lirc restart
 * Stopping remote control daemon(s): LIRC                               [ OK ] 
 * Starting remote control daemon(s) : LIRC                              [ OK ] 
ryan@DVR-Server:/usr/src/lirc-0.8.6$ tail -f /var/log/syslog
Aug  7 12:07:11 DVR-Server lircd-0.8.6[2226]: accepted new client on /var/run/lirc/lircd
Aug  7 12:07:11 DVR-Server lircd-0.8.6[2226]: could not get file information for /dev/lirc0
Aug  7 12:07:11 DVR-Server lircd-0.8.6[2226]: default_init(): No such file or directory
Aug  7 12:07:11 DVR-Server lircd-0.8.6[2226]: Failed to initialize hardware
Aug  7 12:12:35 DVR-Server lircd-0.8.6[2226]: caught signal
Aug  7 12:12:35 DVR-Server lircd-0.8.6[2263]: error in configfile line 61:
Aug  7 12:12:35 DVR-Server lircd-0.8.6[2263]: "2147549184": must be a valid (lirc_t) number
Aug  7 12:12:35 DVR-Server lircd-0.8.6[2263]: reading of file '/etc/lirc//lircd.conf' failed
Aug  7 12:12:35 DVR-Server lircd-0.8.6[2263]: reading of config file failed
Aug  7 12:12:35 DVR-Server lircd-0.8.6[2264]: lircd(default) ready, using /var/run/lirc/lircd
[/B]

[/CODE]

any one have any ideas?

---

### Post by rymonroe on 2010-08-09
I'm getting frustrated. Does anyone know of a separate receiver/blaster that is know to work with 10.04 and a directTV box? I got this HVR-1600 because I thought it was going to be easy to install. If only I knew then what I know now.

---

### Post by rymonroe on 2010-08-12
Mueller...

---

### Post by the_pod on 2010-08-13
Can you provide a link to a pic of the remote?  Curious if its the same one I have.

I have a 1600 and a 1250 (both Hauppauges).  Both have the exact same remote.

I gave up on the IR functionality for these early and had bought a more traditional MCE remote & receiver.  That remote broke about 6 months ago because my 1.5yo daughter was testing to see if it bounced.

Since then, I've managed to get the receiver that came with the MCE remote to work quite well with the two Hauppauge remotes.  I never could get the receivers for the Hauppauges to work. 

Not sure if that gives any aha moments but it's my story. If you think the receiver is working then link to a pic of the remote. I'll check tonight and see what I have the settings at for my remote if its the same one.

---

### Post by rymonroe on 2010-08-13
> **the_pod said:**
> Can you provide a link to a pic of the remote? Curious if its the same one I have.
 
I have a 1600 and a 1250 (both Hauppauges). Both have the exact same remote.
 
I gave up on the IR functionality for these early and had bought a more traditional MCE remote & receiver. That remote broke about 6 months ago because my 1.5yo daughter was testing to see if it bounced.
 
Since then, I've managed to get the receiver that came with the MCE remote to work quite well with the two Hauppauge remotes. I never could get the receivers for the Hauppauges to work. 
 
Not sure if that gives any aha moments but it's my story. If you think the receiver is working then link to a pic of the remote. I'll check tonight and see what I have the settings at for my remote if its the same one.
 
Here is the link to what my remote looks like [www.hauppauge.com/images/new_remote.jpg]("http://ubuntuforums.org/www.hauppauge.com/images/new_remote.jpg") . I really need the blaster to control my directv box. Did the MCE come with a blaster that worked with Ubuntu? Thanks.

---

### Post by ecksiota on 2010-08-19
> **mycatsnameisbernie said:**
> After much trial, error, Googling, and posting on mythtv-users, I finally have my HVR-1600 IR receiver and blaster both working in Lucid 10.04, with all of the grey Hauppauge remote's keys detected. The key to the solution is to use module lirc_zilog, but it's not easy. Here is how I did it:
 

<snip>

Hope that helps...

I would like to report that the approach by mycatsnameisbernie in post #9 (i.e. using lirc_zilog) worked flawlessly for me, as long as I carefully followed the instructions word for word. I have a HVR-1600 IR receiver and blaster set up with Cox Communications (Rhode Island) Motorola DCT2224 box and am happy to say that everything works.

Just one minor comment: when I compiled lirc-0.8.6 with lirc_t typedef'd as unsigned int, the configure step required an option like --with-driver=userspace. Not sure if this is how it was meant to be, but this worked for me.

Thanks for the great instructions mycatsnameisbernie, and Jarod and company for writing the driver.

---

### Post by rymonroe on 2010-08-26
> **ecksiota said:**
> I would like to report that the approach by mycatsnameisbernie in post #9 (i.e. using lirc_zilog) worked flawlessly for me, as long as I carefully followed the instructions word for word. I have a HVR-1600 IR receiver and blaster set up with Cox Communications (Rhode Island) Motorola DCT2224 box and am happy to say that everything works.

Just one minor comment: when I compiled lirc-0.8.6 with lirc_t typedef'd as unsigned int, the configure step required an option like --with-driver=userspace. Not sure if this is how it was meant to be, but this worked for me.

Thanks for the great instructions mycatsnameisbernie, and Jarod and company for writing the driver.

did you have any problems compiling lirc. As mycatsnameisbernie's instructions are wrote, I get an error trying to compile lirc even after I apply the patch. any help would be appreciated.

---

### Post by mycatsnameisbernie on 2010-08-30
> **ecksiota said:**
> I would like to report that the approach by mycatsnameisbernie in post #9 (i.e. using lirc_zilog) worked flawlessly for me, as long as I carefully followed the instructions word for word. 
.
.
.
Just one minor comment: when I compiled lirc-0.8.6 with lirc_t typedef'd as unsigned int, the configure step required an option like --with-driver=userspace. Not sure if this is how it was meant to be, but this worked for me.
.
.
. 
I never ran the configure step directly. I used lirc's setup.sh script to run configure for me.

---

### Post by Janiporo on 2010-09-20
Having a related problem, and started a new thread, because it doesn't quite fit this thread. And this one has parts, that are so hard for me to understand.

My problem is that Ubuntu can not see my Hauppauge (NOVA-T DVB-T) remote as "remote", it sees it as "keyboard". Tried everything I can think of :(
More here --> [http://ubuntuforums.org/showthread.php?p=9866942#post9866942](http://ubuntuforums.org/showthread.php?p=9866942#post9866942)

Please reply to that thread, so I can keep up.

---

