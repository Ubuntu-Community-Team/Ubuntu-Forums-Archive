---
title: "Hauppauge A415-HPG-A Remote Woes in 10.10"
date: 2011-04-03
forum: Mythbuntu
---

### Post by defensorfedei on 2011-04-03
Hey guys.  This post is going to be a long one, but I think it is much needed after all the searching I have done for a solution to this.

I recently converted a Dell Dimension 2400 into a Mythbuntu box, using a Hauppauge pvr-150 I bought second-hand.  It came with the A415-HPG-A remote.  I assumed that since the pvr series Hauppauges are so well supported by myth, that their respective remote controllers would also be well supported.  So far, I have been proven wrong.  I cannot get any functionality out of it at all.

Here is what I have done so far:

1-Installed Mythbuntu 10.10
2- Chose remote option at installation > Hauppauge TV Card w/'Generate Dynamic Button Mappings'
3-configured Myth backend for my cable and card type, etc.... Am able to schedule recordings and watch live TV and all that other good stuff. However, no remote.
4-Open terminal > type 'irw' and then use the remote.  Nothing shows in the terminal.

I have tried the following suggestions at different postings.
[http://ubuntuforums.org/showthread.php?t=1597886&highlight=a415-HPG-](http://ubuntuforums.org/showthread.php?t=1597886&highlight=a415-HPG-)

I didn't get anywhere with this. I am thoroughly confused by many other postings on the net, and really don't know which way to go as far as trouble shooting this.  I am assuming that since the pvr-150 is one of the most popular cards with Linux users, someone has managed to get the included remote to work.  As far as I can tell, the system doesn't recognize that I have a remote at all.

Any help at all would be greatly appreciated.  Judging by the number of posts all over the net, other users would surely appreciate a solution to this problem.

Thanks

---

### Post by defensorfedei on 2011-04-03
This info may help:

Output of 'dmesg | grep lirc'

```
[   17.706336] lirc_dev: IR Remote Control driver registered, major 250 
[   17.743073] lirc_i2c: module is from the staging directory, the quality is unknown, you have been warned.

```This is what my /etc/lirc/lircs.conf file contains:

```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Hauppauge TV card remote:
include "/usr/share/lirc/extras/more_remotes/hauppauge/lircd.conf.hauppauge"

```This is what /etc/lirc/hardware.conf file contains:

```
# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Hauppauge TV card"
REMOTE_MODULES="lirc_dev lirc_i2c"
REMOTE_DRIVER=""
REMOTE_DEVICE="/dev/lirc0"
REMOTE_SOCKET=""
REMOTE_LIRCD_CONF="hauppauge/lircd.conf.hauppauge"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="None"
TRANSMITTER_MODULES=""
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_SOCKET=""
TRANSMITTER_LIRCD_CONF=""
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""


```I hope this info helps anyone who may be able to help.

---

### Post by defensorfedei on 2011-04-03
Here I go replying to myself again. :P  From what I have been able to figure out, I believe that the 'lircd.conf.hauppauge' file does support this remote.  However, what I have found from reading the wiki at mythtv, is that mythtv does not recognize the 'lircd.conf' file out of the box.  Or maybe I am interpreting the wiki incorrectly?  Here is the [Link]("http://www.mythtv.org/docs/mythtv-HOWTO-8.html").

So here are my new questions and concerns.  
1-I see many references that indicate the 'lircd.conf' file should be in the /etc directory.  However, on my system this is not the case......it is in the /etc/lirc directory.  Is the documentation out of date? Or am I missing something?

2-None of what I followed in the mythtv wiki made sense.  The directories they instructed me to go to did not work/exist in my system.

3- If this is a simple matter of telling mythtv where to find the 'lircd.conf' file and how to use it, does anyone have an idea how to do this, so that it makes sense with the way mythbuntu is configured?

4-Is there a way to test and see if your remote signals are actually being received at all?  

4A) I should note here that my ir receiver is actually an ir receiver/blaster combination that connects to the tuner card via a 1/8" headphone jack/plug.....not via usb interface.  Is this a problem that needs extra configuration?

Any suggestions at all would be greatly appreciated.

Thanks

---

### Post by defensorfedei on 2011-04-04
And the plot thickens as I carry on a conversation with myself!

I happened upon this [site]("http://parker1.co.uk/mythtv_ubuntu2.php") and discovered some diagnostic and configuration methods for ir remote controls.  

When I enter this command: 'cat /proc/bus/input/devices' I should get something like this:

```
I: Bus=0001 Vendor=0070 Product=9002 Version=0001
N: Name="cx88 IR (Hauppauge Nova-T DVB-T"
P: Phys=pci-0000:00:0f.0/ir0
H: Handlers=kbd event2
B: EV=100003
B: KEY=108fc000 100822 0 0 0 0 18000 4180 4801 9e0000 7bb80 0 10000000
```Instead I get nothing that mentions my pvr-150.  This to me suggests that the the IR interface on the capture card is not recognized as an input device. I believe that this is the basis of my problem.

Does anyone know how to get the IR interface on a pvr-150 to become recognized as an input device?

Should I stop wasting my time and get a usb IR serial receiver and use my remote this way?

Any comments at all are welcome :P

---

### Post by parker13 on 2011-04-04
Talking to yourself is the first sign of madness...

You posted on my parker1 site asking for help, so here I am, but I have to say that I don't have this remote so cannot be too specific.

I have read a couple of posts which say use the ir-kbd-i2c kernel module instead of lirc_i2c. This may be worth a try:

[http://www.mythtv.org/wiki/Hauppauge_HVR-1600#IR_Remote](http://www.mythtv.org/wiki/Hauppauge_HVR-1600#IR_Remote)

Good luck!

---

### Post by defensorfedei on 2011-04-04
Thank you Parker!  I am going to give this a go and will post back if this brings success.....or not.

---

### Post by defensorfedei on 2011-04-04
NO DICE!!!!!

I think I am possibly experiencing a two-fold problem here.

I definitely think the wiki Parker suggested is relevant, and in fact necessary to get the built-in IR receiver recognized in mythbuntu.  However, the more reading I do, the more I come across the Zilog patch that my first post refers to.  

I am going to try Mythdora, since I have read (in some places) that the Zilog patch is already built into the kernel.

I will post back if I get anywhere.

---

### Post by defensorfedei on 2011-04-04
I have down-graded to 10.04, which for some odd reason works OTB.  9.04 and 9.10 did not (?).  To avoid problems other users have reported in [this post]("http://ubuntuforums.org/showthread.php?t=1294825&highlight=zilog+lirc&page=7"), I disabled update manager and then performed manual updates, EXCLUDING the kernel and lirc updates.  Thus far, this has preserved the system, and all is working great.

As an aside.  I did try the zilog patch prescribed in the post I linked to above in 10.10, but it did not work for me.....not exactly sure why.  

The LIRC guru, Jarod Wilson, has provided an explanation [here]("http://wilsonet.com/?page_id=95") about why there are currently issues in the current kernel 10.10 is shipping with, and there is a thread [here]("http://www.gossamer-threads.com/lists/mythtv/users/455454"), which describes the exact same problem I am having.  

Basically LIRC has been incorporated into the kernel, which has brought about some growing pains, especially on the Ubuntu side of things.  Many of the bugs that are plaguing Mythbuntu 10.10 are non-existent in Mythdora 12.  This is because Ubuntu is a little behind the curve when implementing Jarod's fixes, etc.....as compared to Fedora (Jarod works for Red Hat).

Long story short, this problem should be fixed in later Mythbuntu releases.  Let us keep our fingers crossed.

In case anyone was wondering.....Mythdora worked out of the box for me.  My past memories of instability, coupled with terrible video playback caused me to crawl back to Mythbuntu again.

---

### Post by Daminator on 2011-05-12
I wonder if this is related to the problem I'm having?

Ubuntu 9.x sounds about right for when my Hauppauge remote last worked.

However, 'cat /proc/bus/input/devices' does give me the corect output. I clearly have a Nova-T on event 6 and another on event 7.

---

### Post by defensorfedei on 2011-05-13
I actually ( sort of) followed Parker's guide [here]("http://parker1.co.uk/mythtv_ubuntu.php").  I then installed lirc from the repos and copied a few files and made some symbolic links as described in Parker's tutorial, and everything worked great. I also configured vlc to use lirc and edited my lircrd file for vlc button mappings, so I can have decent dvd playback.  I used 10.04 since it is the longterm support version, and I must say I am very pleased with how well the remote is working now.  I assume that later versions of Ubuntu will eventually fix this issue that now exists in 10.10.

As a side note, my remote does not show up as an input device, but it somehow works.

---

