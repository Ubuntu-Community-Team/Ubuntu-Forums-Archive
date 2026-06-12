---
title: "I need Help"
date: 2010-02-25
forum: Networking &amp; Wireless
---

### Post by wolvie25311 on 2010-02-25
I am an ultra noob. I just downloaded ubuntu 9.10 on my 'puter and I cannot find tyhe drivers for my WUSB100 that will make it work. I keep seeing these post where you have to go edit this line ar drop this sections of lines or change this or that. I have no idea what the "wrapper" is or what lines to look at when I type in the lmsp or whatever that is. I really just need to know what to down load on my puter to make it work correctly.HHHHEEEELLLLLPPPPP!!!!!!!!!!!

---

### Post by chili555 on 2010-02-25
There are a few version of this device. Please let us know which you have by inserting the device and then open Applications -> Accessories -> Terminal and do:```
lsusb
```Post the result and we'll have a better idea of how to proceed.

---

### Post by wolvie25311 on 2010-02-25
I entered lsusb and I got this
Bus oo1 Device 011: ID 1737:0070 Linksys
Bus 001 Device 001:Id Id6b:0001 linux Foundation 1.1 root hub
I have what all that means

---

### Post by chili555 on 2010-02-25
This is supposed to work with a module *rt2870sta*. Let's try:```
sudo modprobe rt2870sta
iwconfig
```Do you now have a wireless interface?

---

### Post by wolvie25311 on 2010-02-25
where do I enter that in?

---

### Post by chili555 on 2010-02-25
Applications -> Accessories -> Terminal

Enter each line and press enter. Enter the next line and press enter. The first command may return nothing, indicating that the command was executed without errors or warnings. The second command will produce some output which we need to see.

---

### Post by wolvie25311 on 2010-02-25
I entered that and I got the message 
Lo              no wireless interface extentions
Ethu           no wireless extentions
wmaster0   no wireless extentions

---

### Post by wolvie25311 on 2010-02-25
do you need the rest of the reply?

---

### Post by chili555 on 2010-02-25
Was there a wlan0 with a lot of text next to it? If so, you now have a wireless interface that can be used to connect. Click the Network Manager icon at the top right and see if you see your network. Select it and connect...hopefully. If you are currently connected with an ethernet cable, you will need to detach the cable first.

---

### Post by wolvie25311 on 2010-02-25
I cannot access the internet from that computer i am using this one to get the answers to fix the other one.

---

### Post by wolvie25311 on 2010-02-25
I got the Wlan4   IEEEE802.11bgn Essid:""
                         Mode managed Req:2.412 ghz Access point: Not Associated
                         Tx-Power=11dBm
                         retry long limit:7 Rtsthr: off Fragment thr: off
                         Power management: on
                         link quality:0 Signal level: 0 Noise level: 0
                         Rx invalid nwid: 0 Rx invalid crypt: 0 Rx invalid Frag: 0
                         Tx excessive retries: 0 Invalid misc: 0 Missed beacon: 0

---

### Post by chili555 on 2010-02-25
Click the Network Manager icon at the top right and see if you see your network. Select it and connect.

---

### Post by wolvie25311 on 2010-02-25
I can locate available networks but they are secured and I cannot locate the network I use for my home computers it isnt giving me that option. Really starting to tick me off now

---

### Post by chili555 on 2010-02-25
I never get ticked off until 25 or 30 posts! I think we can fix this! Let's see if some conflicting drivers are loading and interfering. Please do:```
lsmod | grep rt2
```Please post the result. Thanks.

---

### Post by wolvie25311 on 2010-02-25
how do I enter that? Do I enter lsmod then load grep rt2 or do I enter it all on one line?  And when I enter it what am I looking for?

---

### Post by wolvie25311 on 2010-02-25
I figured out how to enter that and now I just need to know what I am looking for

---

### Post by chili555 on 2010-02-25
You type, in the terminal, lsmod, followed by a space, followed by the pipe symbol | (that is on the right side of my US keyboard, along with \) followed by a space, then grep and a space followed by rt2.

Hit enter.

You will get some output and, depending on what is there and not there, we can tweak you system just a bit to, hopefully, run perfectly, at least respecting wireless.

We hope the module rt2800usb is not loading, along with it's henchmen rt2x00usb and rt2x00lib. If they are loading, they are interfering with rt2870usb which is, I believe, the correct module. 

These conflicts happen sometimes. No operating system is perfect, although some are more perfect than others!

---

### Post by wolvie25311 on 2010-02-25
How will I know if those ones are loading and what do I do if they are

---

### Post by chili555 on 2010-02-25
> How will I know if those ones are loadingRun the command. If they are loaded, they will be listed.> what do I do if they are We will blacklist them and reboot, but let's cross that minor bridge if and when we get to it.

---

### Post by wolvie25311 on 2010-02-25
I went and checked and this is what I found
rt2800usb    37372   o
rt2xoousb    11548   1
rt2xoolib      29756   2

Rt2870usb    488820  0 

What does that mean and what do I do?

---

### Post by chili555 on 2010-02-25
We are going to edit two files. One will always add the module we want and one will blacklist, or prevent, the modules we do not want.```
sudo gedit /etc/modules
```Use nano or kate if you do not have the text editor gedit. Add a new line, on it's own line, by itself:```
rt2870sta
```Proofread carefully. Save and close gedit.```
sudo gedit /etc/modprobe.d/blacklist.conf
```Add three lines, each on their own line:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```By the way, those are zeros, not ohs. Proofread very carefully, save and close gedit. Reboot. Can you now connect?

---

### Post by wolvie25311 on 2010-02-25
how do you blacklist something?

---

### Post by wolvie25311 on 2010-02-25
entered first line and it said command not found. Do I sub the nano ore kate where the gedit is?

---

### Post by wolvie25311 on 2010-02-25
I entered the first set of lines in. Got to the Sudo gedit /etc/modprobe.d/blacklist.comf
typed in the three lines and when I went to save it said it could not find the /etc/modprobe.d/blacklist.comf.

---

### Post by chili555 on 2010-02-25
> sudo gedit /etc/modprobe.d/blacklist.co[COLOR="Red"]n[/COLOR]fSpelling, punctuation and grammar are vital. Please check your work carefully.

---

### Post by wolvie25311 on 2010-02-25
entered it correctly and when I goto save it still says not found?  :(

---

### Post by wolvie25311 on 2010-02-25
AM I still missing something here?  :confused:

---

### Post by chili555 on 2010-02-25
Open a terminal. Enter the following code on one line:```
sudo gedit /etc/modprobe.d/blacklist.conf
```The text editor gedit will open and look like the attached, more or less.

You will type in the three lines as I posted. Then the file will look like the second attachment. Proofread carefully. Click the Save button at the top.  Then go to File -> Quit.

Did it work better?

---

### Post by wolvie25311 on 2010-02-26
Sorry power went off last night. Still couldnt blacklist the lines but I was able to connect but I keep getting disconnected and I have to reset the puter to get reconnected. Is that because of not blacklisting the lines?

---

### Post by wolvie25311 on 2010-02-26
was able to blacklist them and just restarted the puter have to see if it did any good.

---

### Post by wolvie25311 on 2010-02-26
blacklisted them now Ubuntu wont run?????? What did I do wrong and now do I have to reload Ubuntu to correct it

---

### Post by chili555 on 2010-02-26
> now Ubuntu wont runMeaning what? It won't boot to a login screen? It freezes up when you try to connect wirelessly? Or what?

---

### Post by wolvie25311 on 2010-02-26
it boots up but after login screen all it does is show a brown screen. No screen saver no taskbar no nothing. Just an ugly two tone brown screen.

---

### Post by chili555 on 2010-02-26
When you are booting and see a reference to GRUB, press Esc and use the arrow key to go down to the Recovery Mode and see all the lines of code scroll by. See if you can see where it hangs up. If you get to a command prompt, run:```
dmesg | grep -i error
```Make note of what fails and we'll try to fix it.

---

### Post by wolvie25311 on 2010-02-26
ok I reloaded Ubuntu onto that puter and I did the first part of the instructions. I didnt blacklist anything this time and it seems to be working but now I have another interesting question. Will yahoo messenger work on ububtu or do I have to change the settings somewhere to let it work because it doesnt seem to want to load.

---

### Post by chili555 on 2010-02-26
It runs for me! I simply put in my user name and password and connected. I don't know that there is much to change.

---

### Post by wolvie25311 on 2010-02-26
now a new predicament. I was using the ubuntu just fine and it went to do the updates. Well it loaded all the updates to get it current and then said to reset the computer. I did that and now allI have is the little circle on the screen that tells me the puter is thinking. has been doing that now for about 45 min. Am I just doing something wrong or what. I havent changed any setting or anything.

---

### Post by chili555 on 2010-02-26
Are there any other symptoms? Blinking LEDs on the keyboard? I suggest a hard reset by pressing the power button and holding it until it stops. Start again and see if it clears.

---

### Post by wolvie25311 on 2010-02-26
OK that prob is resolved now my archive manager will not let me download the files to have yahoo messenger on the computer keeps telling me that a zipfile is not found or the file is not a zipfile

---

### Post by wolvie25311 on 2010-02-26
this is what I get::
Archive:  /home/william/Downloads/msgr10us(3).exe
[/home/william/Downloads/msgr10us(3).exe]
  End-of-central-directory signature not found.  Either this file is not
  a zipfile, or it constitutes one disk of a multi-part archive.  In the
  latter case the central directory and zipfile comment will be found on
  the last disk(s) of this archive.
zipinfo:  cannot find zipfile directory in one of /home/william/Downloads/msgr10us(3).exe or
          /home/william/Downloads/msgr10us(3).exe.zip, and cannot find /home/william/Downloads/msgr10us(3).exe.ZIP, period.

---

### Post by chili555 on 2010-02-27
I see! You are trying to install Yahoo Messenger with the Windows .exe, which may or may not work, but it requires a program called wine. Even then, not all Windows programs will run successfully or well.

Instead, have you tried Applications -> Internet -> Pidgin?

---

### Post by wolvie25311 on 2010-02-27
so where do I get the wine program?

---

### Post by chili555 on 2010-02-27
Are you sure? wine is not very easy to configure and run. If you insist, please do:```
sudo apt-get install wine
winecfg
```Then run your Windows program with:```
wine your_program.exe
```

Does Pidgin not meet your needs in some respect?

---

### Post by wolvie25311 on 2010-02-27
so do I type wine your_program.exe or wine yahoo_messenger.exe

---

### Post by chili555 on 2010-02-27
```
wine Downloads/msgr10us(3).exe
```Please see: [http://archives.free.net.ph/message/20100202.133233.decf7438.en.html](http://archives.free.net.ph/message/20100202.133233.decf7438.en.html)

As I said, not all Windows programs work well or at all under wine. Good luck and have fun!

---

### Post by chili555 on 2010-02-27
If you have further issues, they may be better answered here: [http://ubuntuforums.org/forumdisplay.php?f=313](http://ubuntuforums.org/forumdisplay.php?f=313)

---

