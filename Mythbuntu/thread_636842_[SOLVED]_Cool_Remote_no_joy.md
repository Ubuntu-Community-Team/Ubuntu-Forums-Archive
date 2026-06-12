---
title: "[SOLVED] Cool Remote no joy"
date: 2007-12-10
forum: Mythbuntu
---

### Post by volkswagner on 2007-12-10
I have a new install of Mythbuntu.  When setting up install I selected MCE remote (used old, and new two separate installs) same end result.

I see a lot of info on .lircrc files yet I do not know where it resides.

I have Gyration Universal Remote Control and Compact Keyboard Suite - Accessory Kit - GYR3101CKUS (no keyboard)  this is RF when in pc mode, but has most all the same buttons as MCE remote thats why I chose it during install.

Problem is most buttons do not work. Working buttons are numeric keys, and direction pad.

When I run irw in a terminal the non-functional buttons do not yield any display.  When I press left navigation button all that is yielded is ^[[D

So the help I am looking for is where do I find my .lircrc file?
Is there a more compatible remote file I should use since this is an RF remote?

Since this is a learning remote I can switch modes and use ir commands, but I would need to add an USB ir reciever and also keep the RF reciever for the built in gyro mouse (way cool and it works)

---

### Post by barney_1 on 2007-12-10
You should be able to use the mythbuntu lirc generator to generate the codes needed for full functionality with that remote.  Check out the community documentation for more info:

[https://help.ubuntu.com/community/Install_Lirc_Gutsy?#head-b79a788f185f0fc4f704b52da6ef68186d5a57b1](https://help.ubuntu.com/community/Install_Lirc_Gutsy?#head-b79a788f185f0fc4f704b52da6ef68186d5a57b1)

---

### Post by volkswagner on 2007-12-10
Thanks for the reply.

I have followed the steps in the link.  The generator was already installed.  I have looked into the .lircrc file and see all the entries for mythtv and other programs.  I don't know what else I can do since the pc does not respond to buttons being pushed.  When running irw in a terminal nothing happens when pressing the buttons that have a problem.  

What am I missing?

---

### Post by barney_1 on 2007-12-11
If you're not getting anything for those buttons then either the frequencies are not listed for them in your /etc/lirc/lircd.conf or the module is not working properly for that remote.

You should try to create your own lircd.conf file.  Make sure you back the current one up first and then use the irrecord command.  Here is a link to the mythtv site concerning irrecord:

[http://lirc.org/html/irrecord.html](http://lirc.org/html/irrecord.html)

once that is created restart lirc and try irw again.  If it worked you will get a readout in irw for those buttons.  Then the mappings must be extended to your lircrc file.

---

### Post by e00 on 2008-01-04
I'm in a similar position.

I bought a MCE remote, works via IR (Sunwave brand remote bought from Altronics in Australia). The number and movement buttons work but the others are kinda random. Thought it might be a matter of setting up the .lircrc file but it seems to be set up ok (selected MCEUSB old style remote on install).

After some digging around and playing with lircd and irw I'm certain now the receiver is being recognised as a USB keyboard. I can confirm it by shutting down lircd and removing all lirc kernel modules (via modprobe) - the remote still works! i.e. I can move the mouse and enter numbers.

Here's the relevant dmesg output:
```

[   33.784567] usbcore: registered new interface driver hiddev
[   33.820021] input: Cypress Cypress USB Keyboard as /class/input/input2
[   33.820086] input: USB HID v1.10 Keyboard [Cypress Cypress USB Keyboard] on usb-0000:00:11.2-2
[   33.820123] usbcore: registered new interface driver usbhid

```

It's also worth noting that the remote is the only USB device attached to the computer.

The question now is: how to stop the thing being seen as a keyboard?

Update: The answer may be to use xev & xbindkeys ([http://ubuntuforums.org/showthread.php?t=595626&highlight=usb+keyboard]("http://ubuntuforums.org/showthread.php?t=595626&highlight=usb+keyboard"))

Update 2: ... or not. Using xev shows my remote outputs multiple key codes for a single button press (e.g. control-L, m). xbindkeys can't associate more than one key code with a command.

---

### Post by volkswagner on 2008-01-04
You may need to reconfigure so the USB device registers a remote not HID keyboard.  I have looked into this and found a possible thread to help.

[http://www.doctort.org/adam/nerd-notes/mythtv-and-the-twinhan-remote.html]("http://www.doctort.org/adam/nerd-notes/mythtv-and-the-twinhan-remote.html")

HTH


If anyone can help me with th Gyration that would be great.  I see the LinuxMCE group has a similar remote with different firmware which works great.  Found this tthread but I don't know if the info is relevant or adaptable.  

[http://forum.linuxmce.org/index.php?topic=2308.0]("http://forum.linuxmce.org/index.php?topic=2308.0")

There is also a bug report 

[https://bugs.launchpad.net/mythbuntu/+bug/156494]("https://bugs.launchpad.net/mythbuntu/+bug/156494")

Not very promising 

:(

---

### Post by e00 on 2008-01-16
The remote (or perhaps the receiver) sends keystrokes set up for Windows MCE. So I rebind some Myth keys and mplayer keys to match and now it all works.

For reference, the list of MCE keys is [http://windowshelp.microsoft.com/Windows/en-US/Help/e69eb36f-de61-4e80-8fe3-f3835b8e3e261033.mspx]("http://windowshelp.microsoft.com/Windows/en-US/Help/e69eb36f-de61-4e80-8fe3-f3835b8e3e261033.mspx"). 

Change the Myth keys for TV playback through the front end via Setup -> Edit Keys, and change the mplayer keys by editing input.conf in /etc/mplayer.

Easy, once you know. :neutral:

---

### Post by volkswagner on 2008-01-16
Glad you were able to get it working.  My problem still exists.  Most keys don't seem to be sending an event in irw.  I tried selecting a remote that was based on RF such as the ATI in mythbuntu list.  When the RF remotes are chosen, irw does not even work "no connection error".  I have found some info on the linuxMCE forums, but I do not know how or if it will apply in mythbuntu.  There is also a bug report.  This is a shame because of the unique function of the gyration remote.

[http://forum.linuxmce.org/index.php?topic=2308.0]("http://forum.linuxmce.org/index.php?topic=2308.0")

[https://bugs.launchpad.net/mythbuntu/+bug/156494]("https://bugs.launchpad.net/mythbuntu/+bug/156494")

Will irrecord even work with an RF remote?  The instructions were way above my head!

:confused:

---

### Post by e00 on 2008-01-23
I know nothing about the Gyration remote, but the symptoms you've described are very similar to the problems I had. 

Your receiver may not register as a keyboard but perhaps it is behaving as such anyway. Instead of sending proper keystroke codes it may be sending ANSI terminal control codes such as the "^[[D" you noted earlier. 

A list of codes is here [http://www.termsys.demon.co.uk/vtansi.htm]("http://www.termsys.demon.co.uk/vtansi.htm") , it may be worthwhile to see if your non-functional keys are sending codes that match some in this list.

Sorry I'm not much help, but I wish you luck!

---

### Post by volkswagner on 2008-02-09
Found this thread.  I was hoping someone here could tell us how to make it work with xfce.

[http://ubuntuforums.org/showthread.php?t=479897]("http://ubuntuforums.org/showthread.php?t=479897")


EDIT:  Well much thanks to Napsilan and the author of EvRouter.  I now have enough function from this remote to be a happy couch potato.  See the above link for the complete story.

---

