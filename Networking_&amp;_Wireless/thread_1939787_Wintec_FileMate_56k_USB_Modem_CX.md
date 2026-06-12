---
title: "Wintec FileMate 56k USB Modem CX?"
date: 2012-03-12
forum: Networking &amp; Wireless
---

### Post by linktopower on 2012-03-12
Okay, I'm running Ubuntu 11.04.
 
I bought a USB Extarnal Modem. Whice is controller based, I think thats a hard ware modem correct me if i'm wrong.

Right now I'm on windows and it shows the manufacturer is "Conexant"
The thing is...how would I be able to use this in ubuntu.
As I know winmodems does not work with linux. hardware modems work.
This is a hardware modem, Now is there a certain modem driver needed or something?

---

### Post by praseodym on 2012-03-12
Please show
> 
lsusb
lsmodwith the device plugged in

---

### Post by linktopower on 2012-03-12
Okay you mean this?

```
benjamin@benjamin-Satellite-A15:~$ lsusb
Bus 002 Device 002: ID 0572:1340 Conexant Systems (Rockwell), Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
benjamin@benjamin-Satellite-A15:~$ lsmod
Module                  Size  Used by
cdc_acm                22150  0 
snd_intel8x0           33213  2 
snd_ac97_codec        105614  1 snd_intel8x0
ac97_bus               12642  1 snd_ac97_codec
snd_pcm                80244  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13132  0 
i915                  450944  2 
snd_rawmidi            25269  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            13213  1 
joydev                 17322  0 
ppdev                  12849  0 
snd_timer              28659  2 snd_pcm,snd_seq
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
pcmcia                 39671  0 
drm_kms_helper         40745  1 i915
yenta_socket           27230  0 
pcmcia_rsrc            18292  1 yenta_socket
snd                    55295  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
drm                   180037  2 i915,drm_kms_helper
psmouse                73312  0 
pcmcia_core            21505  3 pcmcia,yenta_socket,pcmcia_rsrc
soundcore              12600  1 snd
serio_raw              12990  0 
parport_pc             32111  1 
shpchp                 32345  0 
snd_page_alloc         14073  2 snd_intel8x0,snd_pcm
i2c_algo_bit           13184  1 i915
toshiba_acpi           13796  0 
video                  18951  1 i915
sparse_keymap          13666  1 toshiba_acpi
lp                     13349  0 
parport                36746  3 ppdev,parport_pc,lp
e100                   40108  0 

```
Is this it?

---

### Post by praseodym on 2012-03-13
See here

[http://www.linuxant.com/drivers/dgc/index.php](http://www.linuxant.com/drivers/dgc/index.php)

---

### Post by linktopower on 2012-03-13
> **praseodym said:**
> See here

[http://www.linuxant.com/drivers/dgc/index.php](http://www.linuxant.com/drivers/dgc/index.php)

Okay I have the driver installed. But may I ask what do I do next to dial out.

And Thanks for helping me find a driver for me :)

---

### Post by praseodym on 2012-03-13
Try the "DSL" section of the network-manager or some different dial-program like "gnome-ppp"

---

### Post by linktopower on 2012-03-13
> **praseodym said:**
> Try the "DSL" section of the network-manager or some different dial-program like "gnome-ppp"
Well, I just got it working now. I had to use the generic usb drivers. but after doing that wvdial pick up the configration and work just great :).
I have to say thank you so much :) for the help. I've been trying and trying and I finally got it working.
Heck I'm on ubuntu right now :P

---

### Post by mofomofo on 2012-04-05
hello guys please i have the sam problem "the problem is the driver " i tried to use it from the site could not figure it out plzz any help

---

### Post by linktopower on 2012-04-05
> **mofomofo said:**
> hello guys please i have the sam problem "the problem is the driver " i tried to use it from the site could not figure it out plzz any help

okay hello. before I might be able to help. I would like to know what ubuntu version you are using. 
and if you know what Kernal version are you using?

---

### Post by TheStrategist on 2012-07-16
> **linktopower said:**
> okay hello. before I might be able to help. I would like to know what ubuntu version you are using. 
and if you know what Kernal version are you using?
Hi linktopower,

I've just decided to make the switch from Windows Xp and Windows 7 to Ubuntu 12.04 myself, however I too am in the same situation where Ubuntu isn't recognizing the external modem.  If you're still willing to help a fellow dial-up user out ;) , here is my info...

These are the same details that you requested of mofomofo in a previous post.  This is it for my system...

Ubuntu Version: Ubuntu 12.04 Precise Pangolin
Kernel Version: 3.2.0-23-generic-pae

Thanks in advance!!

---

### Post by dobby818 on 2012-07-22
me too. please i'm begging

---

### Post by linktopower on 2012-07-22
> **dobby818 said:**
> me too. please i'm begging
If you are using Ubuntu 12.04, I would recomend Downgrading you r kernal of the Os with an Older Kernal.
I found out any kernal past 2.6.38-10 will not let install the driver.

So you'll have to install

linux-headers-2.6.38-10_2.6.38-10.46_all.deb
linux-headers-2.6.38-10-generic_2.6.38-10.46_i386.deb
linux-image-2.6.38-10-generic_2.6.38-10.46_i386.deb
 
After that Restart you computer and hold shift to gain ascess to the boot-loader.
Just choose the old kernal you just installed and 
Install the driver

dgcmodem_1.13_i386.deb

After that all you have to do is
```
dcgconfig
```
and you modem should be installed. After that you will need Wvdial installed to and set up.
after you do that just Open the console and type
```
Sudo su
```

```
wvdial
```

And you should be able to dial out.
And don't forget to set up wvdail just type this
```
gedit wvdial.conf
```
and then all you have to do is put in
```

[Dialer Defaults]

Modem=/dev/ttyUSB0
Baud=115200
Dial Command = ATDT
Baud=115200
Dial Command = ATDT
init1=ATZ
init2=AT+CRM=1
Flow Control= Hardware (CRTSCTS)
Username =
Password =
Phone = #777
Stupid Mode = 1
```

---

### Post by dobby818 on 2012-07-23
how do i install the first three things

---

### Post by TheStrategist on 2012-07-23
> **dobby818 said:**
> how do i install the first three things
dobby818, in order to install the files, make a directory and put all three files in it. 

Then simply do " sudo dpkg -i *.deb" while in the directory where you put the files.  

They will all install automatically. :)

---

### Post by TheStrategist on 2012-07-23
Hey linktopower, I appreciate you getting back to us, and giving us this guide on how to get it working :)

I'm going to start testing it out in a VM and see how it goes first, then maybe on my real computer.

As you can imagine, downloading these files on dial-up is going to take a few hours (about 3 hours with 45mb at 5kb/s), although if it means internet connectivity, then so be it lol.

I'll keep you guys updated on how it goes.

Cheers! :D

---

### Post by dobby818 on 2012-07-24
i'm still a little confused with the whole dictionary thing, i have only been using ubuntu for about a month, and i'm still learning

---

### Post by praseodym on 2012-07-24
Save the files in "Downloads" and install via terminal (CTRL+ALT+T):

> sudo dpkg -i ~/Downloads/linux-*.deb

---

### Post by linktopower on 2012-07-24
~Update~ I forgot to say some things right. So here is the updated how to?

If you are using Ubuntu 12.04, I would recommend Downgrading your kernel of the Os with an Older Kernel.
I found out any kernel past 2.6.38-10 will not let install the driver.

So you'll have to install

linux-headers-2.6.38-10_2.6.38-10.46_all.deb
linux-headers-2.6.38-10-generic_2.6.38-10.46_i386.deb
linux-image-2.6.38-10-generic_2.6.38-10.46_i386.deb
 
After that Restart you computer and hold shift to gain ascess to the boot-loader.
Just choose the old kernal you just installed and 
Install the driver

dgcmodem_1.13_i386.deb

After that all you have to do is
```
dcgconfig
```and you modem should be installed. After that you will need 

Wvdial installed to and set up.
after you do that just Open the console and type

```
Sudo su
``````
wvdial
```
And you should be able to dial out. 

And don't forget to set up wvdail just type this
```
gedit gedit /etc/wvdial.conf
```
and then all you have to do is put in
Make sure that the /dev/, says ttyACM0 and not USB0
(Sorry I didn't get a chance to look at my Linux OS ti find out how to do it.)

```

[Dialer Defaults]

Modem=/dev/ttyACM0
Baud=115200
Dial Command = ATDT
Baud=115200
Dial Command = ATDT
init1=ATZ
init2=AT+CRM=1
Flow Control= Hardware (CRTSCTS)
Username =
Password =
Phone = #777
Stupid Mode = 1
```

NOTE: If you can not use gedit on your Wvdial.conf just do
```
sudo su
```
then run whatever file manger you are running, and make your way to The "File system" and then locate the folder Etc.
Look for the wvdial.conf and then edit.

______________________________________________________

@dobby818:  Its not a  dictionary its a Directory. which in terms is a folder. etc,

@TheStrategist: Yeah I know the files are quite big it took me a while to download them too XD


And One more NOTE: If anyone has any problems with doing this for any reason. I would recommend try using, Ubuntu 11.04 OR Linux Mint 12. These are the two Os's I've tried with dial up so far. From what I gather that any thing based of Ubuntu dhould work though. (I can't say it works on Ubuntu 12.04 though sorry I've haven't taken the time to try Ubuntu 12.04.

---

### Post by TheStrategist on 2012-07-25
linktopower, I tested it out on my system which was running one of the newer 3.2.0-23 kernels.  I was able to downgrade fine, and all works great :)  

I'm going to post a guide of how everything works and how others can do it too.

---

### Post by TheStrategist on 2012-07-25
Hey guys,

I figured since I was able to get everything working on my system (thanks to linktopower, and other ubuntu users), I would post a short guide as well to help out anyone else who has been having the same issues.  The solution to everything basically involves downgrading your linux kernel.

These are my system specifications: 

Ubuntu Version: Ubuntu 12.04: Precise Pangolin
Kernel Version: 3.2.0-23-generic-pae

Basically the situation is that the Conexant gdc modem drivers at Linuxant are about two years old.  

The reason that we have been experiencing build errors is because their  code is old.  So we have essentially been trying to  compile their old code build for older kernels, to run on our newer  kernel.


In order to get the driver to work, we have two options.

[LIST=1]
[*]Downgrade our kernel to the last one supported by their old driver.
[*]Recompile their driver to work with newer kernels.
[/LIST]
If  you absolutely want to be able to get internet access via dial-up right  away, then the first option of downgrading the kernel is what you will  need to do.


WARNING: Downgrading to the 2.6.38-10-generic kernel broke support for  my wireless driver.  However since you will be able to choose which  kernel you wish to run at start up, your newer kernel will still be able  to do wireless.


In order to downgrade your kernel, you need to download three things:

[LIST=1]
[*][linux-headers-2.6.38-10_2.6.38-10.46_all.deb]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-10_2.6.38-10.46_all.deb")
[*][linux-headers-2.6.38-10-generic_2.6.38-10.46_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-headers-2.6.38-10-generic_2.6.38-10.46_i386.deb")
[*][linux-image-2.6.38-10-generic_2.6.38-10.46_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-2.6.38-10-generic_2.6.38-10.46_i386.deb")
[/LIST]
(I linked each one to the right file, so all you have to do is click them to download)

Once you have downloaded all three of those files, make a directory on  your desktop and name it "oldkerneldebs", then put those three files in  that folder.

Simply open up a terminal window by pressing [Ctrl]+[Alt]+[T]


In the terminal window, type:
```
pwd 
```(in order to display the current directory that you're in)


Since you've just opened the terminal, you should be in the default directory of:


 /home/username/


Now simply  navigate to your desktop and into that folder.  This is  accomplished by  typing in these commands into your terminal:

```
cd Desktop
cd oldkerneldebs

```After that, type in:

```
sudo dpkg -i *.deb
```(This tells the system to install all the  deb files which are installed in the directroy "oldkerneldebs".)

After that, you will see walls of text, which are the files installing.   When they finish installing, simply restart your computer. 

Before Ubuntu boots back up, make sure to hit the [Shift] key (it was  the right shift key for me, although you can try the left one, or both  at the same time, whichever works for you.) so that it will load the GNU  GRUB bootlogger.

If you are dual booting anyway, you can likely skip that step, because GRUB loads by default.

Once the bootlogger loads up, it will display an option of all the  operating systems to choose from.  You should see a list similar to  something like this:

[LIST=1]
[*]Ubuntu, with Linux 3.2.0-23-generic-pae
[*]Ubuntu, with Linux 3.2.0-23-generic-pae (recovery mode)
[*]Previous Linux Versions
[*]Memory Test (memtest86+)
[*]Memory Test (memtest86+, serial console 115200)
[/LIST]
From that list, choose #3, which is Previous Linux Versions.


Once clicking that, there will be a screen which displays two options:

[LIST=1]
[*]Ubuntu, with Linux 2.6.38-10-generic
[*]Ubuntu, with Linux 2.6.38-10-generic (recovery mode)
[/LIST]
Select the first option which is Ubuntu, with Linux 2.6.38-10-generic.


After that Ubuntu will boot up normally.  If all went like it should,  you should be running the 2.6.38-10-generic kernel now.  To make sure  that you are, open up a Terminal window [Ctrl]+[Alt]+[T] and type:


```
uname -r
```It should now say : 2.6.38-10-generic


If so, then you have successfully downgraded your kernel.  You can now  choose at system start up the kernel that you wish to use.


Now before you reinstall the driver, lets make sure that you uninstall  everything that you've done before when trying to get things to work.


Simply open up a terminal window by pressing [Ctrl]+[Alt]+[T]

In the terminal window, type: 
```
sudo dgcconfig --uninstall
```(This will remove all configurations pertaining to the modem driver)

Again, in the terminal window, type:
```
pwd 
```(in order to display the current directory that you're in)


Since you've just opened the terminal, you should be in the default directory of:


 /home/username/


If the dgcmodem-1.13 folder was extracted to your desktop, simply  navigate to your desktop and delete that folder.  This is accomplished  by typing in these commands into your terminal:

```
cd Desktop
sudo rm -r dgcmodem-1.13

```(This will delete the entire folder including all files and sub-directories.) 

After that is done, find the file dgcmodem-1.13.tar.gz and put it on  your desktop.  Extract it again to your desktop as well.  This can be  done by either the command line, or right clicking on the  dgcmodem-1.13.tar.gz file and selecting the option "Extract Here".

Once it's extracted, switch back into your terminal and type in: 
```
cd dgcmodem-1.13
```(In order to move into the newly extracted directory)

Once inside the directory, type in: 
```
sudo make install
```(This will compile and install the driver for you)

During that process, a lot of text will scroll the screen, then you will be prompted with this message: 

"Where is the linux source build directory that matches your running kernel?
[/lib/modules/2.6.38-10-generic/build]"

When you see that message, don't type anything, just hit the Enter key and let it continue.

You will then see the the message:

"Building modules for kernel 2.6.38-10-generic, using source directory 
/lib/modules/2.6.38-10-generic/build.  Please wait...
done."

If you see the word "done" then congratulations, you just install the  modem correctly.  If not, retrace your steps and make sure you followed  the instructions correctly.

---

### Post by linktopower on 2012-07-25
@TheStrategist: That's great news! I'm glad I was able to help you all out. And with the "How to" You just wrote It should help so many other users that are trying use there Dial up On Linux :).

This should help many users in the future!

---

### Post by TheStrategist on 2012-07-25
> **linktopower said:**
> @TheStrategist: That's great news! I'm glad I was able to help you all out. And with the "How to" You just wrote It should help so many other users that are trying use there Dial up On Linux :).

This should help many users in the future!
@linktopower:  Hey glad I could help :) .  I figured it was the least I could do since I was in the same boat only a few days ago myself.  It was really a team effort though, and i'm glad to just be able to contribute to the open source community.

I suppose after a few days of having these post up, if no one responds to them or needs anymore help, we can mark it as [SOLVED]  :)

---

### Post by TheStrategist on 2012-07-26
**MAJOR UPDATE!!**

Good news guys, a good friend of mine who goes by the name  [Computator]("http://ubuntuforums.org/member.php?u=1235469") on the UbuntuForums did me the HUGE favor of creating a patch that allows the driver to work with the latest kernels.

So you don't have to downgrade your kernels anymore, the driver will work with the latest kernel now.

This was accomplished by utilizing and implementing a special patch he made for the driver.

You can get the patch by clicking --> [Patch]("http://derekthewriter.com/ubuntu/fixes/dgcmodem-1.13.patch") <--

In order to get the driver working, you simply install the patch before you compile and install the driver.

So it's essentially:

```
sudo patch -p1 < dgcmodem-1.13.patch
sudo make install
```I couldn't have done this without my buddy [Computator]("http://ubuntuforums.org/member.php?u=1235469"), so everyone make sure to give him a shoutout and a thank you :)

---

### Post by linktopower on 2012-07-27
Holy sh*t this is the best thing I've heard all day! I'll be giving this a try tomorrow! I've always been wanting to use the new kernals!

Thanks TheStrategist! and Computator!!!

---

### Post by Computator on 2012-07-27
Thanks guys :)

---

### Post by TheStrategist on 2012-07-27
Glad we could help :) 

Yeah the 2.6 kernel actually broke my wifi, plus I hate to have to use old stuff just to get one feature to work properly.  

The patch seems to work just fine, and i'm actually on wireless dial-up right from using the driver/patch.  So all is good.

This will hopefully make it much easier for everyone who has had this issue.

Cheers!!

---

### Post by linktopower on 2012-07-27
I've just tried the patch on Linux Mint 12 (Note its the same as Ubuntu 11.10) With the new kernel.
And 100% Success! now we can stop downgrading to older kernals forever! <3

---

### Post by linktopower on 2012-07-28
You know I've been having a strange issue with the new patch On Ubuntu 12.04 Lts.

I can do the patch. But When I get it installed and I go to finish the install of the driver with 
```
dgcconfig
```
And it pretty much fails... and says it error could build modules.

Now This is my first time trying it Ubuntu 12.04, But it seems I might doing something wrong <_<

Note I tried installing multiple times and same result every time any ideas On whats going wrong?

---

### Post by beerhat on 2012-07-29
> **linktopower said:**
> You know I've been having a strange issue with the new patch On Ubuntu 12.04 Lts.

I can do the patch. But When I get it installed and I go to finish the install of the driver with 
```
dgcconfig
```
And it pretty much fails... and says it error could build modules.

Now This is my first time trying it Ubuntu 12.04, But it seems I might doing something wrong <_<

Note I tried installing multiple times and same result every time any ideas On whats going wrong?

Same OS, but under esxi5.  I get past the dgcconfig without problems.. but there's no modem device added.  hmmmmm..  and dmesg has nothing interesting either.

---

### Post by Computator on 2012-07-29
I made the patch on 12.04 but it should work with any. All the patch does is replace the deprecated locking code with the new versions. If you are still getting the error building the modules you may have patched it incorrectly, otherwise it should work on newer kernels.

---

### Post by linktopower on 2012-07-30
@Computator: Maybe I did patch it wrong I'm not sure. I had it working once with no issue but... Something stupid I did Killed Unity and I had to re-install. after that I kept getting Build errors... even on the new Install of Ubuntu 12.04

Huh I just wonder why it won't work now. I can do it on Linux Mint 12 just fine but not Ubuntu 12.04... Now that's just plain weird

---

### Post by beerhat on 2012-07-30
> **linktopower said:**
> @Computator: Maybe I did patch it wrong I'm not sure. I had it working once with no issue but... Something stupid I did Killed Unity and I had to re-install. after that I kept getting Build errors... even on the new Install of Ubuntu 12.04

Huh I just wonder why it won't work now. I can do it on Linux Mint 12 just fine but not Ubuntu 12.04... Now that's just plain weird

What was the modem device assigned down /dev on Mint??  

I'm running 12.04 server (via ESXi5), and I was able to patch it correctly and it looked to install just fine.  I just don't see any device label that would indicate the presence of a modem.  lsusb does show the modem however.

Bus 001 Device 005: ID 0803:3095 Zoom Telephonics, Inc.

---

### Post by linktopower on 2012-07-30
@beerhat: The Modem was assigned as  device "ttyACM0" That's what it is always signed as every time I do it on Mint 12 or Ubuntu 11.04
Is that what you wanted to know?

---

### Post by beerhat on 2012-07-30
> **linktopower said:**
> @beerhat: The Modem was assigned as  device "ttyACM0" That's what it is always signed as every time I do it on Mint 12 or Ubuntu 11.04
Is that what you wanted to know?

yeah.  thanks.  rats.  not there on my 12.04 box. grrrr...

I'm not ruling out problems manifesting with the esxi usb passthrough.  Guess I'll have to grab an old laptop and do a quick native 12.04 install.

Thanks again.

Dan

---

### Post by TheStrategist on 2012-07-31
@linktopower

Did you try doing: 

```
sudo dgcconfig --uninstall
```Then deleting the extracted folder of the modem, extracting the folder again from the tar.gz file, reapplying the patch and compiling it again?

Btw, it's recognizing my modem as a "ttyACM0" as well, although all is working fine for me so far.

---

### Post by dobby818 on 2012-07-31
i tried to do the codes for the patch, and they r not working. everything that i have tried has become an epic fell.

---

### Post by linktopower on 2012-08-01
@dobby818:
Are you trying to install from the source? or what?
If you are installing from the source with the patch needs (At least I think it does)
You have to download the .tar.gz File of the driver and extract the files from the .tar and then take the patch file and put it in the folder you just extracted. and then after that you'll have to open the folder on in the terminal and perform
```

sudo patch -p1 < dgcmodem-1.13.patch
sudo make install

```and that should do something.

And if you cannot patch the file and ubuntu is saying you need a patcher just install this program.
[http://packages.ubuntu.com/en/precise/utils/patch](http://packages.ubuntu.com/en/precise/utils/patch)

And then you should be set. maybe I'm not sure, I hope that it'll will.

EDIT: Wow finally got the driver to work on Ubuntu 12.04 <_<.
I'm on it right now and everything is working fine and dandy now... I wonder why it worked now randomly?

---

### Post by linktopower on 2012-08-04
Some weird stuff is happening to me lately... 

Okay with the patch on Ubuntu 12.04 I was able to install the modem on my laptop and be able to get online.

But I try on my desktop and the modem driver installs just fine.
It even dials up with wvdial. But the craziness starts here, After performing (On my desktop mind you)
```
sudo wvdial
```
It connects as far as I tell, but I try to get online with Firefox and fire fox says its not connected to the internet. and I can't do anything.

Now I thought it was Ubuntu 12.04, So I picked up Zorin core OS-6. and tried it on there with the same results(Connects but I can't browse online)
For some weird reason this is happening <_< 
**So Anyone has any ideas on why this is happening?**

---

### Post by TheStrategist on 2012-08-04
> **linktopower said:**
> Some weird stuff is happening to me lately... 

Okay with the patch on Ubuntu 12.04 I was able to install the modem on my laptop and be able to get online.

But I try on my desktop and the modem driver installs just fine.
It even dials up with wvdial. But the craziness starts here, After performing (On my desktop mind you)
```
sudo wvdial
```
It connects as far as I tell, but I try to get online with Firefox and fire fox says its not connected to the internet. and I can't do anything.

Now I thought it was Ubuntu 12.04, So I picked up Zorin core OS-6. and tried it on there with the same results(Connects but I can't browse online)
For some weird reason this is happening <_< 
**So Anyone has any ideas on why this is happening?**
@linktopower

Have you tried anything else other than Firefox to try it out with?  It's possible that Firefox may be in "Offline" mode.

You can try to install software or get updates via the terminal and see if the connection works.

Also, you may want to try Gnome PPP as the frontend app to wvdial.  That's what I use to get all my network configurations for dial-up set in place.

---

### Post by linktopower on 2012-08-05
> **TheStrategist said:**
> @linktopower

Have you tried anything else other than Firefox to try it out with?  It's possible that Firefox may be in "Offline" mode.

You can try to install software or get updates via the terminal and see if the connection works.

Also, you may want to try Gnome PPP as the frontend app to wvdial.  That's what I use to get all my network configurations for dial-up set in place.

Yeah I've tried Chromium too, sam results can't get online at all, Heck I haven't even tried using apt to test the connection. (Don't know why I didn't try that)
And You know I haven't even tried using Gnome PPP yet I need to try that as well. I'll be back later to post my results.



**EDIT:**
Well I tried Gnome PPP, and no dice... And also tried apt-update to test the connection but its fails. (No internet connection found)

I even downgraded the Kernal and no dice again <_______< 
I don't know whats the deal with any OS built off of Ubuntu 12.04 but its something wrong with it. 
I might move away from its unstable butt :P and go back to Linux Mint 12... (man I really wanted to run the new version, Oh well My Linux Cool mint 12 will be back on my computer in awhile so... yeah...

---

### Post by kidoruigenso on 2012-08-20
Hello linktopower,

On post 37 you state: "Wow finally got the driver to work on Ubuntu 12.04", apparently using the patch of Computator found at [http://derekthewriter.com/ubuntu/fixes/dgcmodem-1.13.patch](http://derekthewriter.com/ubuntu/fixes/dgcmodem-1.13.patch) combined with the generic source tar package from [http://www.linuxant.com/drivers/dgc/downloads.php](http://www.linuxant.com/drivers/dgc/downloads.php). 

On post 40 it looks like all failed.

Both posts edited ~two weeks ago.   What was your final outcome?

If this post is solved it will be great news for those of us using dialup and wanting to keep the latest kernel.

---

### Post by linktopower on 2012-08-22
> **kidoruigenso said:**
> Hello linktopower,

On post 37 you state: "Wow finally got the driver to work on Ubuntu 12.04", apparently using the patch of Computator found at [http://derekthewriter.com/ubuntu/fixes/dgcmodem-1.13.patch](http://derekthewriter.com/ubuntu/fixes/dgcmodem-1.13.patch) combined with the generic source tar package from [http://www.linuxant.com/drivers/dgc/downloads.php](http://www.linuxant.com/drivers/dgc/downloads.php). 

On post 40 it looks like all failed.

Both posts edited ~two weeks ago.   What was your final outcome?

If this post is solved it will be great news for those of us using dialup and wanting to keep the latest kernel.

Well it seems when I made that last post here, I messed something up on Ubuntu 12.04, and my computer acted like it was not connected at all. But after a complete re-install
and changing my location to the Louisville, Kentucky (I live in Tennessee) some reason its not on the list of locations on the setup area on Ubuntu 12.04, I kept putting TN in and some how It messed up.
But after setting my location to Louisville, Kentucky in the ubuntu 12.04 setup
My dial up works on it now.

So Final outcome, as long as you use one the preset locations in the Ubuntu setup. Setting up the dial up with the patch everything will work just fine.

---

### Post by Pierr on 2013-01-18
The link to the patch [http://derekthe](http://derekthe) writer.com/ubuntu...  no longer works.  Does anyone know where I can get this patch so I can get my modem working?  Many thanks.

---

### Post by TheStrategist on 2013-01-18
Hi Pierr,

Yeah sorry about that, I didn't remember to move the patch after I switched vps servers and got a different domain name.  Anyways, here is the updated link to the patch.

Patch: [http://strat.vm.ionfish.org/patches/dgcmodem-1.13.patch](http://strat.vm.ionfish.org/patches/dgcmodem-1.13.patch)

Thanks.

---

### Post by Pierr on 2013-01-19
Hello TheStrategist

Thank you for coming back on this so quickly.

The link you provided works great and now my modem is detected.  I don't know how you guys do it but am really thankful for your efforts.    All I need to do is battle with seeing how I can get that dialler to work.

Thanks again so much.:D

---

### Post by TheStrategist on 2013-01-21
> **Pierr said:**
> Hello TheStrategist

Thank you for coming back on this so quickly.

The link you provided works great and now my modem is detected.  I don't know how you guys do it but am really thankful for your efforts.    All I need to do is battle with seeing how I can get that dialler to work.

Thanks again so much.:D
Hi Pierr, 

No problem man, glad to help :)

As for the dialer working, I just use Gnome-PPP with wvdial.  If I remember correctly, Wvdial may come with Gnome-PPP(not 100% sure though, so check up on that.)

Good luck

Cheers!

---

### Post by Pierr on 2013-01-23
Hello TheStrategist,

Indeed I managed to use Gnome-ppp and I can confirm Wvdialler comes with it.

With the Zoom 3095 modem plugged in to the PC, in terminal I downloaded and installed by typing:

sudo apt-get install gnome-ppp

Then I had to reboot to get gnome ppp to recognise a modem was installed.

After that I filled in my ISP details username, password and phone number, but I was being disconnected after 10 seconds.

So I found I had to start this  application, just the once, from terminal by typing:

gksudo gnome-ppp

This did the trick and now I can go straight to the gnome-ppp without using terminal and not get disconnected after 10 seconds.

So I am a happy chap got my Zoom 3095 modem working with Unbuntu 12.04 which I never thought would happen without your help and the help any others on this forum.

A big thanks to you and all that I can confirm this all works great:D.

---

### Post by TheStrategist on 2013-01-23
> **Pierr said:**
> Hello TheStrategist,

Indeed I managed to use Gnome-ppp and I can confirm Wvdialler comes with it.

With the Zoom 3095 modem plugged in to the PC, in terminal I downloaded and installed by typing:

sudo apt-get install gnome-ppp

Then I had to reboot to get gnome ppp to recognise a modem was installed.

After that I filled in my ISP details username, password and phone number, but I was being disconnected after 10 seconds.

So I found I had to start this  application, just the once, from terminal by typing:

gksudo gnome-ppp

This did the trick and now I can go straight to the gnome-ppp without using terminal and not get disconnected after 10 seconds.

So I am a happy chap got my Zoom 3095 modem working with Unbuntu 12.04 which I never thought would happen without your help and the help any others on this forum.

A big thanks to you and all that I can confirm this all works great:D.
Hi Pierr,

I'm happy you were able to get everything working on your system.

Glad we could help :)

---

### Post by TheStrategist on 2013-01-23
> **linktopower said:**
> Well it seems when I made that last post here, I messed something up on Ubuntu 12.04, and my computer acted like it was not connected at all. But after a complete re-install
and changing my location to the Louisville, Kentucky (I live in Tennessee) some reason its not on the list of locations on the setup area on Ubuntu 12.04, I kept putting TN in and some how It messed up.
But after setting my location to Louisville, Kentucky in the ubuntu 12.04 setup
My dial up works on it now.

So Final outcome, as long as you use one the preset locations in the Ubuntu setup. Setting up the dial up with the patch everything will work just fine.
Looks like everything seems to be working well for everyone now. 

I'm guessing we can mark this post as solved now :)

---

### Post by andyee on 2013-05-27
> **TheStrategist said:**
> Hi Pierr,

Yeah sorry about that, I didn't remember to move the patch after I switched vps servers and got a different domain name.  Anyways, here is the updated link to the patch.

Patch: [http://strat.vm.ionfish.org/patches/dgcmodem-1.13.patch](http://strat.vm.ionfish.org/patches/dgcmodem-1.13.patch)

Thanks.

Did anyone can update the link of patch again?  I cannot find any working link for the patch

---

### Post by TheStrategist on 2013-06-05
Hi andyee,

Once again, the same thing pretty much happened with me buying a new VPS server, and forgetting to move the file.  Sorry about that guys.

Anyways, here is the patch: [http://199.127.226.221/patches/ubuntu/dgcmodem-1.13.patch](http://199.127.226.221/patches/ubuntu/dgcmodem-1.13.patch)

Thanks.

---

### Post by TheStrategist on 2014-01-13
Just for the record, I wanted to state that my friend [Computator]("http://ubuntuforums.org/member.php?u=1235469") on UbuntuForums is the creator of this patch :-)  I use to host the file on derekthewriter.com which I let expire, so moved it to a new server.

Anyone that this patched helped out and allowed to get their modem working, please give a shoutout to him instead ;D Thanks.

---

### Post by jcs12301 on 2014-02-26
Does anyone have the patch available to share? The latest link doesn't work.

Thanks.

---

### Post by TheStrategist on 2014-02-26
Hi jcs12301, sorry about the missing link to the file.  I just decided to upload it to a public server on MediaFire so it won't go missing anymore.  

Here is the link: [http://www.mediafire.com/download/tiqoawvjh6aw6yl/dgcmodem-1.13.patch](http://www.mediafire.com/download/tiqoawvjh6aw6yl/dgcmodem-1.13.patch)

---

### Post by jcs12301 on 2014-02-27
Thank you so much for your quick response, TheStrategist.
Sadly it seems something else has changed. gdcconfig fails because asm/system.h does not exist. :(

Thank you anyway!

---

### Post by TheStrategist on 2014-02-27
No problem bud.  

What version of Ubuntu are you running?  At the time, I was running Ubuntu 12.04 LTS, but when switching to Ubuntu 13.10, there were many complications with it.  I ended up just buying a new modem from Amazon that was Linux compatible and plug in play.  Works very well too.

Check it out: [http://www.amazon.com/gp/product/B004BU8O9Y/ref=oh_details_o04_s00_i01?ie=UTF8&psc=1](http://www.amazon.com/gp/product/B004BU8O9Y/ref=oh_details_o04_s00_i01?ie=UTF8&psc=1)

---

### Post by jcs12301 on 2014-02-27
This is also Ubuntu 12.04 LTS, but with kernel 3.5.0-46.

Thanks for the recommendation, I think I'll follow that route too.

---

### Post by ejubkadric on 2014-07-16
Hello everyone.
I got the patch, and I copied it into the folder in which the content of .tar.gz package was extracted before.
I opened the terminal, entered the patching command,and the patching was successful, and I got these messages:
"patching file modules/osdcp.c
patching file modules/mod_dgcusbdcp.c"

After that I typed in "sudo make install" and terminal did the installation and asked me to enter "dgcconfig" to finalize the installation. When I entered "dgcconfig" it said:

"Trying to automatically build the driver modules...
(this requires a C compiler and proper kernel sources to be installed)

Where is the linux source build directory that matches your running kernel?
[/lib/modules/3.5.0-52-generic/build] "

And I pressed enter. After this I got the build error:
"ERROR: Module build failed!
Please examine the log file "/tmp/dgcconfig-buildlog.txt" to determine why."

---

### Post by praseodym on 2014-07-16
Did you install the headers?
```

sudo apt-get install --reinstall linux-headers-$(uname -r)
```

---

### Post by ejubkadric on 2014-07-17
Yes I did. Same thing happens.

---

### Post by andyee on 2014-07-29
thanks

---

### Post by paul218 on 2015-07-20
Hi all,

I was following through this thread trying to find the patches and get dgcmodem-1.13 from linuxant to build, however it seems that my Conextant based modem (branded Zoom) is now working without this driver on my 3.16 kernel. It seems to be using a module called cdc_acm.

I know the thread is old but maybe this note will help others like me still reading it whilst trying to get an old USB modem working!

Paul

---

