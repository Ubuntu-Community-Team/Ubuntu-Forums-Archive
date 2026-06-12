---
title: "Cannot activate Broadcom STA driver"
date: 2010-01-10
forum: Networking &amp; Wireless
---

### Post by RJKinsman on 2010-01-10
Hello, I need help with wireless networking using Ubuntu Netbook Remix on my Dell Inspiron Mini 10.  I've read many posts, but can't find one describing the problem I'm having.  I've installed the Broadcom STA driver following the instructions provided by nallen00 in [http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699).  

After that, the STA driver is not activated, and I can't seem to get it activated.  

I attached a screenshot showing the driver installed but not activated.

Here are details from terminal commands:

rjkinsman@rolands-netbook:~$ sudo lshw -C network
[sudo] password for rjkinsman: 
  *-network UNCLAIMED     
       description: Network controller
       product: BCM4312 802.11b/g
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:d8000000-d8003fff

rjkinsman@rolands-netbook:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

rjkinsman@rolands-netbook:~$ iwconfig
lo        no wireless extensions.

rjkinsman@rolands-netbook:~$ lsmod
Module                  Size  Used by
binfmt_misc             8356  1 
ppdev                   6688  0 
snd_hda_codec_intelhdmi    12860  1 
snd_hda_codec_realtek   203328  1 
snd_hda_intel          26920  2 
snd_hda_codec          75708  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
uvcvideo               59080  0 
videodev               36736  1 uvcvideo
v4l1_compat            14496  2 uvcvideo,videodev
snd_hwdep               7200  1 snd_hda_codec
snd_pcm_oss            37920  0 
snd_mixer_oss          16028  1 snd_pcm_oss
snd_pcm                75296  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           2656  0 
snd_seq_oss            28576  0 
snd_seq_midi            6432  0 
snd_rawmidi            22208  1 snd_seq_midi
snd_seq_midi_event      6940  2 snd_seq_oss,snd_seq_midi
snd_seq                50224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              22276  2 snd_pcm,snd_seq
snd_seq_device          6920  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
lp                      8964  0 
snd                    59204  17 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
dell_wmi                2564  0 
compal_laptop           3728  0 
soundcore               7264  1 snd
snd_page_alloc          9156  2 snd_hda_intel,snd_pcm
parport                35340  2 ppdev,lp
psmouse                56180  0 
serio_raw               5280  0 
dcdbas                  7292  0 
i2c_isch                4160  0 
iptable_filter          3100  0 
ip_tables              11692  1 iptable_filter
x_tables               16544  1 ip_tables
usb_storage            52544  0 
video                  19380  0 
output                  2780  1 video

rjkinsman@rolands-netbook:~$ iwlist scan
lo        Interface doesn't support scanning.

rjkinsman@rolands-netbook:~$ lsb_release -d
Description:    Ubuntu 9.10

rjkinsman@rolands-netbook:~$ uname -mr
2.6.31-14-generic i686

rjkinsman@rolands-netbook:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                    [ OK ] 

Any help would be greatly appreciated!

---

### Post by ahood on 2010-01-10
Not sure if I can help.

We have a Dell Mini 10v and successfully installed 9.10 and the Broadcom STA driver.

What happens if you click on the 'Activate' button in the screenshot posted?

If you receive an error message, what does it say?

---

### Post by peterthewolf on 2010-01-10
Dont bother with unr - full karmic installs without problems.

---

### Post by RJKinsman on 2010-01-10
> **ahood said:**
> What happens if you click on the 'Activate' button in the screenshot posted?

If you receive an error message, what does it say?

Good question.  I should have mentioned this in my initial post.  When I click on 'Activate' nothing happens.  No errors, no change.  I'm very new to Ubuntu, so I'm not sure if I should expect it to become active instantly, but it doesn't.  When I re-boot, same thing, no change.

---

### Post by RJKinsman on 2010-01-10
> **peterthewolf said:**
> Dont bother with unr - full karmic installs without problems.

OK, I can try that.   At this point, UNR is no good to me without wireless.  I'l post the results in around 6 hours.   I'm in US Central time zone.  I'm at church right now, not by my computer.

---

### Post by tlcstat on 2010-01-10
Greetings,
When activating the driver you should have the Karmic CD in you drive and your drive listed as a software source under System/Administration/Software Sources. Else the driver won't be able to activate. 
FYI
tlcstat

---

### Post by RJKinsman on 2010-01-10
> **tlcstat said:**
> you should have the Karmic CD in you drive 

OK, that's a good lead.  I am ready and willing to try that.  One problem.  It's a netbook.  No CD drive.  I installed UNR from a bootable USB flash drive.  

Any ideas how to do that with a flash drive?

---

### Post by tlcstat on 2010-01-10
Greetings,
It doesn't matter where your install CD is located, it can even be on a network drive. Just add the path to your Preferred Software Sources and Ubuntu will automatically index and use the install files from where ever they are located.
tlcstat

Greetings,
One more thing. After you add the path to your sources be sure to click the update link so the sources database will update to include your new path.
tlcstat

---

### Post by RJKinsman on 2010-01-10
OK, I'm sorry to be so dense, but I'm not seeing what you're talking about.  I'm attaching a screen shot of "Software Sources."  I can't figure out on this dialog where to add the USB drive as a "preferred software source," and I don't see "update link"  Does the screen shot help you help me?  

Thanks again!  I sure hope this works.

---

### Post by tlcstat on 2010-01-10
Greetings,
With your USB drive mounted open your USB drive and then copy the address line in your file browser. Open Software Sources and choose "Other Software" then choose "ADD" at the bottom.
Paste the address that you clipped from your file browser into the APT line. When finished you can click the Update button at the bottom. 
tlcstat

---

### Post by RJKinsman on 2010-01-10
OK, well I'm getting different results, but still no satisfaction!  Thanks for sticking with me.  

So I copied the address of the USB drive into "APT line" but the "Add Source" would not become enabled.  Then I naively prefixed the address with "deb" as the dialog suggests.  That allowed the "Add Source" button to be enabled, and got the USB disk on the list.  I'm attaching a screen shot showing what I entered (1.APT Line.png) and the results (2.Other Software.png).

I attempted to activate the driver, with no visible results.  When I re-booted, there was an alert icon in the top bar.  I'm attaching a screen shot (3.Alert message.png).  When I right-clicked and chose "Check for updates" I got an error.  I'm attaching a screen shot of that (4.Malformed line 54 error.png).

Thanks again, tlcstat, for your help so far!

---

### Post by tlcstat on 2010-01-10
Greetings,
Open a terminal and type "sudo apt-get install bcmwl-kernal-source" without the quotes of course.
Let me know what results you get.
tlcstat

Greetings,
Just so you will know the above command will install the supporting infrastructure for the Broadcom chipset.
tlcstat

---

### Post by soju on 2010-01-10
Ok I try to follow, but it wont except the apt line - i have 2 partitions on the pendrive!? or other possible reasons? -sry im an english noob ^^

---

### Post by RJKinsman on 2010-01-10
OK, well, with all due respect, I think we're starting to go in circles here.  I've been down that path, as I stated in the initial post.  

Nevertheless, here are the results of the install command:

```
rjkinsman@rolands-netbook:~$ sudo apt-get check
[sudo] password for rjkinsman: 
E: Malformed line 54 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
rjkinsman@rolands-netbook:~$ sudo apt-get install bcmkwl-kernal-source
[sudo] password for rjkinsman: 
E: Malformed line 38 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
rjkinsman@rolands-netbook:~$ sudo apt-get install bcmkwl-kernal-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcmkwl-kernal-source
rjkinsman@rolands-netbook:~$ sudo apt-get install bcmkwl-kernal-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package bcmkwl-kernal-source

```So I went back and navigated to  pool -> restricted -> b -> bcmwl on the live USB, and ran the install there, as documented in the post I cited in my initial post.  It says, "same version already installed."  I'm attaching a screen shot of that (bcmwl-kernel-source install.png).

As I stated in my initial post, the driver is installed.  I just can't get it to activate.

Thanks again for your patience and attempts to help.

---

### Post by tlcstat on 2010-01-10
Greetings,
I'm not sure of the path to put in the APT line for software sources on a USB drive. Since I am new at this myself, looks like we will have to hope a pro steps in and gives the correct instructions. I do know that the driver won't activate unless it has access to that software source directory on the CD/USB. I just fix the same problem on my Wife's Dell this morning. The only difference is that my Install drive is on a CD and not USB. Attention all of you Linux pros ..... do you know the correct procedure for adding the installation disk to the Software Sources if it is on USB instead of CD? Please help. Thanks in advance.
tlcstat

---

### Post by RJKinsman on 2010-01-10
I found the Windows recovery CD for my computer.  I'm very frustrated, and going to revert to something that works.

---

### Post by tlcstat on 2010-01-10
Greetings,
Linux isn't for the easily frustrated. A command line has to be written correctly in Windows also. Best of luck on your new adventure. PS When you load Windows, don't forget to install an antivirus and spyware blocker.
tlcstat

---

### Post by RJKinsman on 2010-01-10
I gave it my best shot.  I don't think I would characterize my experience with Linux as "easily frustrated."  Have you seen the number of posts about this driver?  Give me a break.  Great malware protection -- yeah-- no connection at all.  That will protect you.  Easily frustrated my eye.

---

### Post by tlcstat on 2010-01-10
Greetings,
At least Ubuntu put the wifi drivers on the install CD. The reason for all the posts is that computer users all over the planet are installing Ubuntu themselves instead of having it preinstalled by the OEM. There is a learning curve to any operating system and software also. This is why I retired at age fifty-eight as a Windows business consultant. I spent ten years hunting down drivers for Windows installations. But just because I have years of experience at the professional level with Windows I didn't think I could switch to linux and not have to bump heads. That is why I waited until I was retired to give it a try. So far very pleased. 
PS you have a simple command line issue in your Software Sources. I wouldn't give up so easy.
Best regards
tlcstat

---

### Post by hovrashko on 2010-01-10
[SIZE=3][RJKinsman]("http://ubuntuforums.org/member.php?u=990211") try ubuntu 9.04, i have the same issue on 9.10 but not on 9.04 x64,  then you can upgrade to 9.10.
  makes sense?

regards,
   Eric[/SIZE]

---

### Post by hovrashko on 2010-01-11
> **RJKinsman said:**
> I gave it my best shot.  I don't think I would characterize my experience with Linux as "easily frustrated."  Have you seen the number of posts about this driver?  Give me a break.  Great malware protection -- yeah-- no connection at all.  That will protect you.  Easily frustrated my eye.

[SIZE=3]poor guy, I sympathize you, has been struggling 1 day, wow!! :D

here are:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)  - download and install according to the README.

if you don't know how - let me know i lay it for you in dummy edition,


;)

regards,
  Eric[/SIZE]

---

### Post by usenetz on 2010-01-11
> **tlcstat said:**
> When activating the driver you should have the Karmic CD in you drive and your drive listed as a software source under System/Administration/Software Sourcestlcstat, 

I have also been having this [Broadcom STA driver]("http://ubuntuforums.org/showthread.php?p=8622383#post8622383") problem with Linux Mint on a MacBook Pro 5,5 using a BCM4322 802.11a/b/g/n Wireless LAN Controller (rev 01)) and following your advice resolved it for me. :P

Thank-you

john

---

### Post by ahood on 2010-01-18
> **RJKinsman said:**
> I found the Windows recovery CD for my computer.  I'm very frustrated, and going to revert to something that works.

Much apologies for the late reply.

I know RJKinsman has moved on, so my post may be of benefit to other Ubuntu users that stumble upon this thread.

From the screenshot in the previous post, it appears that RJKinsman was successful in installing the wireless driver. 

However, it still seemed not to work.

I wonder if it didn't work was because the device was actually turned off.

It must be kept in mind that the Dell Mini 10 does not have any indicator that the wireless device is working, except for the OS. However, if the device has been turned off via the keyboard, then the OS behavior will not change.

I don't know if RJKinsman tried, and unfortunately I was not around to suggest, pressing the keys on the keyboard that toggles the wireless device on the Dell Mini.

Oh well.

---

### Post by tlcstat on 2010-01-18
Greetings, Actually that is a good point. Our cat turned off my wife's wifi and it took me about three hours to figure out what happened. He doesn't say if he is using a secure network but if so he might simplify the troubleshooting process by turning off security. I use mac addressing in my router and I find that to be much less trouble. I put in the mac address for each of my computers and printers etc and I don't need to fool with the encryption. 
FYI
tlcstat

---

### Post by armoftheland on 2010-02-11
Thanks to tlcstat for the great help. using apt-get install patch and adding wl to new line fixed the problem, but we never would have gotten our hp mini to connect wirelessly without your brilliant advice to ensure a route to start up disc/usb drive. THANKS!!!!

---

### Post by xxGrenxx on 2010-02-12
ive had an issue with the broadcom freezin my compooter but in case anyone else has had that issue seems to be solved with reinstalls...

---

### Post by Ad1217 on 2010-07-06
After an update, my dell mini 9's internet stopped working. I tried the instructions on this forum and many others, but nothing worked. After poking around, I saw an error in apt-get about the kernel source not being installed. I installed it, (sudo apt-get install linux-source-2.6.32) purged the broadcom packages (sudo apt-get purge b43-fwcutter bcmwl-kernel-source bcmwl-modaliases broadcom-sta-common broadcom-sta-source), and ran jockey-gtk. To my surprise and delight, the activation worked!:)

---

