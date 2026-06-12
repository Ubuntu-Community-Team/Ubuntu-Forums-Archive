---
title: "Guide - IR Remote for XBMC 02/2011"
date: 2011-02-24
forum: Multimedia Software
---

### Post by tbridges42 on 2011-02-24
I've spent most of the day on setting up a remote in XBMC through Ubuntu and Lirc, and due to the many problems I encountered, I decided to create a more comprehensive and up-to-date guide than any I found in my searches. The number one problem I found is that a search, whether in Google or in forums like this one, is as likely to turn up results from 2005 for Feisty as it is modern responses. The best existing guide seems to be the Ubuntu Community Guide for LIRC, as it should be, but that also has some problems.

So, this guide was created 02/24/2011, for Ubuntu 10.04LTS, Lirc 0.8.6 and XBMC 10.0 r35648. I SSH into my media center, so this is all in terminal.

First of all, you need a remote with an IR receiver. I picked up one of [these]("http://www.mymediagear.com/products/id_12.html") for $15 at Micro Center. I'm not sure I recommend it because it was far from plug-n-play, but it was cheap.

Make sure your remote has charged batteries in it, and is functioning. Usually when you plug in the receiver correctly it will blink, and when you push a button on the remote both the remote and the receiver blink. Believe it or not this cost me twenty minutes, so double check. If possible, confirm all buttons work on a Windows system. Ensure the receiver is plugged in properly.

Next, install Lirc
```
sudo aptitude install lirc
```When you install the current version of Lirc, it pops up a configuration window. If your remote has a green Windows logo on it, select "Windows Media Center Transceivers/Remotes (all)" followed by "Microsoft Windows Media Center V2 (usb) : Direct TV Receiver". The Direct TV bit is unimportant. As far as I know any of that set will work, but I haven't tested. Press enter, and the installation is done.

If you chose the wrong options at install, you can change later with ```
sudo dpkg-reconfigure lirc
```Next test the installation with <i>irw</i>. No options are necessary. When you run irw, the console will appear to hang. Press buttons on on your remote, and hopefully things will appear on the terminal. If they look like

```
000000037ff07bf3 00 Power mceusb
000000037ff07be1 00 Up mceusb
000000037ff07bde 00 Right mceusb
000000037ff07bdd 00 OK mceusb
```and one appears for every button you press, you're in good shape and can skip to setting up XBMC. If you're like me, nothing happens at all. Either way, exit with ctrl-c.

Nothing Happened
If nothing happened, double-check that the remote and receiver appear to be working. Then ensure Ubuntu is recognizing your receiver. To do this, type *lsusb*. You'll see a list of all USB devices. If you're lucky, one of them says something about being an IR receiver. If you're me, they're all obscure and arcane haiku. If the latter is true, unplug your receiver and run *lsusb* again. The line that went away is your receiver. On that line there will be Bus blah Device blah: ID blah:blah Company name Item description. Write down blah:blah and the Company name. In my case it's 147a:e037 Formosa.

Next you'll need the source code:
```
sudo aptitude install lirc-modules-source
```Navigate to /usr/src/lirc-0.8.6/drivers/lirc_mceusb. Use your favorite editor to open lirc_mceusb.c. Scroll way down until you see lines like #define VENDOR_MITSUMI 0x03ee. Check and see if your company name is there. If it's not, you'll need to add it. follow the convention #define VENDOR_COMPANY 0xblah, where blah is the first half of blah:blah from *lsusb *above. Once it's there, go to the next stanza, and look for your remote. They're in alphabetical order by company. If you don't see it, you'll need to add it. Go ahead and comment in a name (that's the /* blah */ part. Then the next line should be <code>{ USB_DEVICE(VENDOR_COMPANY, 0xblah) }, where COMPANY is the one word company name you used in the #define stanza, and blah is the second half of blah:blah from *lsusb* above.

Save and exit, and then we'll need to rebuild lirc. To do that, first remove the old module:
```
sudo dkms remove -m lirc -v 0.8.6 --all
```then build the new one:
```
sudo dkms add -m lirc -v 0.8.6
sudo dkms -m lirc -v 0.8.6 build
sudo dkms -m lirc -v 0.8.6 install
```And update and reinstall

```
sudo rmmod lirc_mceusb
sudo modprobe lirc_mceusb
sudo /etc/init.d/lirc restart
```Finally, run *irw *again. Hopefully codes are now popping up when you press buttons. Exit with ctrl-c again, and proceed to the next step.

Everything Works
If lirc is working, all that's left is to map buttons to actions in XBMC. First, run *irw* one last time, press every button on your remote, and record, including capitalization, the name of every button. For instance, in mine they're things like Up, Home, etc. They may be more arcane in yours.

Go to /$HOME$/.xbmc/userdata. Here you will need to create a file called Lircmap.xml. The format for this file is

```
  <lircmap>
       <remote device="devicename">
               <XBMC_button>LIRC_button</XBMC_button>
               ...
       </remote>
  </lircmap>
```where devicename is mceusb if you've been following this guide, LIRC_button is exactly the name from irw, such as Up or bAck, and XBMC button is a variable defined in keymap.xml. A table of most of these buttons is [here]("http://wiki.xbmc.org/index.php?title=Keymap.xml#Remote_Section"). So, for example, my up button is listed as ```
<up>Up</up>
``` When you have all of your buttons coded in, save this file, and load XBMC. That should be it.


I'm a relative Linux n00b still, and everything above I taught myself today by searching various forums, the Ubuntu Community Doc, the XBMC wiki, and through generous trial and error. If you see any problems or have anything useful to add, pertaining to the current releases of these programs, please comment. Feedback is appreciated. But all in all, I'd rather not clutter up this thread, so future generations of n00bs don't have to dig through pages of threads like I did.

---

