---
title: "How to Blacklist iwl3945 driver correctly, and replace/whitelist it with ipwraw??"
date: 2009-03-27
forum: Networking &amp; Wireless
---

### Post by scrypt on 2009-03-27
Forgive me if i am not fully clear when i say whitelist.

What i know for sure that I need to do is Blacklist this driver:

    iwl3945

I also Need to make this driver the new replacement for the removed above driver: This is why i say whitelist (Opposite to blacklist):

     ipwraw

I have managed to do it numerous times,
BUT, each time I reboot ubuntu. Itseems to reset it back to it to the original driver???

I am still pretty new to Ubuntu, So could somebody give me clear doncise step bt step instructions how I can Do the above??

Thank-you

scrypt

---

### Post by chili555 on 2009-03-27
You need to do what I asked you to do in the other thread. Did you?

Why start a new thread?

---

### Post by scrypt on 2009-03-27
I use this set of commands...But do they contradict themselves???

Am I blacklisting the driver ipwraw
and then loading it again a couple of commands later??

Should I be blacklisting the iwl3945 driver instead?

Is this why The drivers are loading the original iwl3945 driver??

sudo apt-get install build-essential (get core files)
sudo apt-get install libssl-dev (get supporting library)
wget [http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2](http://dl.aircrack-ng.org/drivers/ipwraw-ng-2.3.4-04022008.tar.bz2) (downloads driver)
tar -xjf ipwraw-ng* (extract the archive file)
cd ipwraw-ng (go to the extracted folder)
make (compile the source files into a binary)
sudo make install (install the driver)
sudo make install_ucode
echo "blacklist ipwraw" | sudo tee /etc/modprobe.d/ipwraw (blacklist the default ipwraw)
sudo depmod -ae (create a dependency file for the modules)
sudo modprobe -r iwl3945 (unload driver that you do not need)
sudo modprobe ipwraw (load the driver that you installed)
sudo ifconfig wlan0 up (enable the network adapter)
airmon-ng start wlan0 (put your interface into monitor mode)

Can someone clear this up for me??

---

### Post by chili555 on 2009-03-27
Did I not answer that clearly enough in post #26 here? [http://ubuntuforums.org/showthread.php?t=1108363&page=3](http://ubuntuforums.org/showthread.php?t=1108363&page=3)

Did you do as I suggested? I will be glad to go through it once again if you feel it's not clear.

---

### Post by scrypt on 2009-03-27
Hey chili.

Yes i think you did mate.

I can get my card running in monitor mode okay.

that is until I reboo and my original driver is back as it was originally...

---

### Post by chili555 on 2009-03-27
Please post:```
cat /etc/modprobe.d/blacklist
cat /etc/modprobe.d/ipwraw
cat /etc/modules
```Thanks.

---

### Post by scrypt on 2009-03-27
I would appreciate i if you would go throgh it again step by step and see if you can see where i am going wrong. I am having the same problem over and over.

It resets the drivers as soon as i reboot??

---

### Post by scrypt on 2009-03-27
mark@ubuntu:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.


# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# Conflicts with dvb driver (which is better for handling this device)
blacklist snd_aw2

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801

# replaced by p54pci
blacklist prism54

# replaced by b43 and ssb.
blacklist bcm43xx

# most apps now use garmin usb driver directly (Ubuntu: #114565)
blacklist garmin_gps

# replaced by asus-laptop (Ubuntu: #184721)
blacklist asus_acpi

# low-quality, just noise when being used for sound playback, causes
# hangs at desktop session start (Ubuntu: #246969)
blacklist snd_pcsp

blacklist iwl3945


mark@ubuntu:~$ cat /etc/modprobe.d/ipwraw
blacklist ipwraw
mark@ubuntu:~$ cat /etc/modules

---

### Post by chili555 on 2009-03-27
My post on the other thread asks you to edit */etc/modprobe.d/ipwraw* to change it to:```
#blacklist ipwraw
```Please do so.

I also asked you to amend */etc/modules* to add:```
ipwraw
```Please do so.

Does this:> mark@ubuntu:~$ cat /etc/modulestell me that you ran the command and ***nothing*** appeared? There is a lot of stuff that is supposed to be in there.

After a reboot, run:```
lsmod | grep iwl
```What happens?

> mark@ubuntu:~$ cat /etc/modprobe.d/blacklistThis one is perfect!!!

---

### Post by scrypt on 2009-03-27
how to I edit this: edit /etc/modprobe.d/ipwraw

What do i use to edit this?

Also how do I amend amend /etc/modules?



Im a big newbie Chili (plz chil chili) :)

im not really sure wha you mean by this, sorry,

Please do so.

Does this:
Quote:
mark@ubuntu:~$ cat /etc/modules
tell me that you ran the command and nothing appeared? There is a lot of stuff that is supposed to be in there.

After a reboot, run:
Code:

lsmod | grep iwl

What happens?

Quote:
mark@ubuntu:~$ cat /etc/modprobe.d/blacklist
This one is perfect!!!

---

### Post by scrypt on 2009-03-27
I ran this gedit /etc/modprobe.d/ipwraw and then added a # before bleclistiwl3945

---

### Post by chili555 on 2009-03-27
Open a terminal. Type:```
sudo gedit /etc/modules
```Give your passwrord. A text editor will appear with the file in it. Make the changes I requested. Proofread your work. If you are old and half-blind like me, proofread it twice. Press 'Save' and close gedit. Go on to the other changes we need the same way.> Im a big newbieNo prob. We are all learning, even old gray-bearded Chili.```
cat /etc/modules
```Please post the result when you enter this in a terminal and press that magic 'Enter' key.

---

### Post by scrypt on 2009-03-28
I think i sussed it.

I ran  sudo gedit /etc/modprobe.d/blacklist and added a # before blacklist.

I then ran  sudo gedit cat /etc/modules  then added ipwraw

then saved thrm both then quit.

Was I correct to do so??

Please have a think back to what it was like when you first stated out with Ubuntu...

This is how i feel..

This ones perfect...

---

### Post by chili555 on 2009-03-28
Almost perfect. In */etc/modprobe.d/blacklist* you need to make sure that:```
blacklist iwl3945
```appears ***without*** a #. Please check and edit if needed.> I then ran sudo gedit cat /etc/modules then added ipwrawIt is not *sudo gedit [COLOR="Red"]cat[/COLOR] /etc/modules*. It is:```
sudo gedit  /etc/modules
```Try again. As long as *ipwraw *is in there, on its own line, _without_ any #, then you are fine. Reboot and then, in a terminal, run:```
lsmod | grep iwl
```Puh-leeeeeeeeeeze tell me what happens!

Bedtime. I will check on you first thing tomorrow.

---

### Post by scrypt on 2009-03-28
This is what I got from the  'lsmod | grep ipw' cmomand

also this is what I got from the  'lsmod | grep iwl' command

after a reboot:

mark@ubuntu:~$ lsmod | grep ipw
ipwraw                125848  0 

mark@ubuntu:~$ lsmod | grep iwl

Here is the output from the 'cat /etc/modules' command

mark@ubuntu:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
ipwraw

mark@ubuntu:~$ cat /etc/modprobe.d/ipwraw
#blacklist ipwraw
mark@ubuntu:~$ lsmod | grep iwl
mark@ubuntu:~$ 

And when I type this command into the terminal 'lsmod | grep iwl'

I get nothing show up just a new prompt?

It looks like this:

mark@ubuntu:~$  lsmod | grep iwl
mark@ubuntu:~$ 

Has it gone according to plan?? was it successful?

I look forward to your replies tomorow?

Thank's agian Chili...

---

### Post by scrypt on 2009-03-28
cat /etc/modprobe.d/ipwraw

mark@ubuntu:~$ cat /etc/modprobe.d/ipwraw
#blacklist ipwraw

---

### Post by scrypt on 2009-03-28
mark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     unassociated  ESSID:off/any  
          Mode:Monitor  Channel=1  Bit Rate=54 Mb/s   
          
rtap0     no wireless extensions.

pan0      no wireless extensions.

i have got my card into monitor mode, BUT now i cannot sem to get any siganl too or from it.

im nearly there though Chili. not doing bad for a brgginer

where have i gone wrong??

---

### Post by chili555 on 2009-03-28
> Has it gone according to plan?? was it successful?It sure looks like it to me. The new driver ***is*** loading and the old driver ***is not*** loading. You have a wireless interface, *wifi0* that goes into monitor mode.

I know nothing about packet injection so I can't help you there. Your original objective, to kick *iwl3945 *out and to load *ipwraw* is working.

---

### Post by scrypt on 2009-03-28
Hi ya chili..

Thank's alot for you perseverance!

---

### Post by scrypt on 2009-03-28
I cannot put my card back inti managed mode for surfing the net do you know how to put it back to managed mode?

I get this when i use the iwconfig command:

mark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     unassociated  ESSID:off/any  
          Mode:Monitor  
          
rtap0     no wireless extensions.

pan0      no wireless extensions

I should be getting this output:

lo no wireless extensions.

eth0 no wireless extensions.

wmaster0 no wireless extensions.

wlan0 IEEE 802.11abg ESSID:"ROUTER"
Mode:Managed Frequency:2.437 GHz Access Point: 00:1E:74:6C:22:96
Bit Rate=54 Mb/s Tx-Power=15 dBm
Retry min limit:7 RTS thrff Fragment thr=2352 B
Encryption key:2387-BFEE-4C96-8850-5522-9F08-8314-43B8-3BD9-D7A9-1E56-0F13-0ACF-1D8B-4869-2D6C [2] Security modepen
Power Managementff
Link Quality=98/100 Signal level:-26 dBm Noise level=-62 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0


rtap0 no wireless extensions.

pan0 no wireless extensions.

I seem to have no wireless network what so ever.

can you help me sort this chili?

I have had no other replies...

---

### Post by scrypt on 2009-03-28
I use this to try to enable my card:

sudo ifconfig wlan0 up

What is the correct way to enable the wireless card
and i cannoy put the card back into managed mode

---

### Post by chili555 on 2009-03-28
First of all, I don't understand why you think you should be getting an interface *wlan0.* In the package you extracted, there is a document, *README.ipwraw-ng*. It clearly refers to *wifi0.*> I left the default speed at 54 MBit. You may want to lower it to 1 MBit before injection with iwconfig wifi0 rate 1M.

To get your card into managed mode, I would try opening a termial and doing these commands, in order:```
sudo ifdown wifi0
sudo iwconfig wifi0 mode managed rate 54M
sudo ifup wifi0
sudo iwconfig wifi0
```Did 'managed' mode stick?

---

### Post by scrypt on 2009-03-28
Hi ya Chili, glad your back.

yes I get that now..
Right ive got what i wanted, which is for my sytem to load with the new driver SORTED. Thanks Chili...

mark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     unassociated  ESSID:off/any  
          Mode:Monitor  Channel=1  Bit Rate=54 Mb/s   
          
rtap0     no wireless extensions.

pan0      no wireless extensions

BUT I try to use some other commands from to do with network vulnerability and package injection...

and I do not seem to have any sort of siganl too or from my wireless card?

I think it is not enabled?

Can you assist Chili??

---

### Post by scrypt on 2009-03-28
Monitor mode is what is loading at bootup.

I am also NOT able to switch between Monitor or Managed mode??

---

### Post by scrypt on 2009-03-28
I will try the commands to try to get my card into managed mode??

Should my card be turned of befor using the commands??

---

### Post by scrypt on 2009-03-28
mark@ubuntu:~$ sudo ifdown wifi0
[sudo] password for mark: 
ifdown: interface wifi0 not configured
mark@ubuntu:~$

---

### Post by chili555 on 2009-03-28
> Should my card be turned of befor using the commands??Do you mean with the wireless switch on the computer? It should be turned ***on*** at all times.> mark@ubuntu:~$ sudo ifdown wifi0
[sudo] password for mark:
ifdown: interface wifi0 not configured
mark@ubuntu:~$ And then what happened when you continued on with the other commands?

---

### Post by scrypt on 2009-03-28
Hello Chili.

Here is the output from the last set of commands you gave me:

mark@ubuntu:~$ sudo ifdown wifi0
ifdown: interface wifi0 not configured
mark@ubuntu:~$ sudo iwconfig wifi0 mode managed rate 54M
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device wifi0 ; Resource temporarily unavailable.
mark@ubuntu:~$ sudo ifup wifi0
Ignoring unknown interface wifi0=wifi0.
mark@ubuntu:~$ sudo iwconfig wifi0

I am begining to feel quite a bit lost by it. Can you give me a little more help?

---

### Post by chili555 on 2009-03-28
Please let me see the output of these two commands:```
ifconfig -a
iwconfig
```Thanks.

---

### Post by scrypt on 2009-03-28
mark@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:a0:d1:45:a7:e6  
          inet addr:192.168.0.2  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2a0:d1ff:fe45:a7e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2471 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2224 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2546477 (2.5 MB)  TX bytes:441950 (441.9 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 B)  TX bytes:100 (100.0 B)

pan0      Link encap:Ethernet  HWaddr 86:cf:00:1a:8c:15  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

rtap0     Link encap:UNSPEC  HWaddr 00-13-02-7D-B5-38-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wifi0     Link encap:UNSPEC  HWaddr 00-13-02-7D-B5-38-00-00-00-00-00-00-00-00-00-00  
          BROADCAST MULTICAST  MTU:2346  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Memory:da000000-da000fff 


mark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     unassociated  ESSID:off/any  
          Mode:Monitor  Channel=1  Bit Rate=54 Mb/s   
          
rtap0     no wireless extensions.

pan0      no wireless extensions.

---

### Post by chili555 on 2009-03-28
Have you read the README's in the package you extracted? Are you at all certain that ipwraw will even do 'Managed' mode? I am not very certain.

You could always do:```
sudo rmmod -f ipwraw
sudo modprobe iwl3945
sudo ifup wlan0 mode managed rate 54M
```When you reboot, because of the settings we set up, it will revert to *ipwraw* in 'monitor mode.

---

### Post by scrypt on 2009-03-28
Valid point Chili.

I will give the last set of commmands a try?

Can you give me the set of commands to put it back into monitor mode

Then I will know how to change between Managed and monitor mode, pretty quickly?

Also How can I check to make sure my Card Is giving out a signal in Monitor mode?

---

### Post by scrypt on 2009-03-28
I ask this because I could run the below commands and get output that package injection was successfull.

But I know get that It is UNSuccessfull.

That is why i think my card is not configured correctly?

mark@ubuntu:~$ sudo aireplay-ng -9 wifi0
[sudo] password for mark: 
21:49:20  Trying broadcast probe requests...
21:49:22  No Answer...
21:49:22  Found 0 APs

---

### Post by chili555 on 2009-03-28
To go back to monitor mode is simply the reverse:```
sudo ifdown wlan0
sudo rmmod -f iwl3945
sudo modprobe ipwraw
```

---

### Post by chili555 on 2009-03-28
> **scrypt said:**
> I ask this because I could run the below commands and get output that package injection was successfull.

But I know get that It is UNSuccessfull.

That is why i think my card is not configured correctly?

mark@ubuntu:~$ sudo aireplay-ng -9 wifi0
[sudo] password for mark: 
21:49:20  Trying broadcast probe requests...
21:49:22  No Answer...
21:49:22  Found 0 APsSorry, I know nothing about paket injection. Please read the README and check any FAQs from the website where you got the package.

You might also, now, start a new thread, "How do I enable packet injection with ipwraw."

---

### Post by scrypt on 2009-03-28
sure okay.

I ran these and rebooted:

sudo rmmod -f ipwraw
sudo modprobe iwl3945
sudo ifup wlan0 mode managed rate 54M

here is the iwcongig output now

mark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

But I still have no wireless connectivity to the net?

---

### Post by scrypt on 2009-03-28
As I have said earlier. I am newish to Ubuntu, So I set myself a task of testing one of my own Home network for vulnerabilities?

Not only will I learn a bit about networks. I am also learning about using ubuntu as-well!!

---

### Post by chili555 on 2009-03-28
> **scrypt said:**
> sure okay.

I ran these and rebooted:

sudo rmmod -f ipwraw
sudo modprobe iwl3945
sudo ifup wlan0 mode managed rate 54M

here is the iwcongig output now

mark@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

But I still have no wireless connectivity to the net?No need to reboot. Remember what I said?> When you reboot, because of the settings we set up, it will revert to ipwraw in 'monitor mode. Please run the commands:```
sudo rmmod -f ipwraw
sudo modprobe iwl3945
sudo ifup wlan0 mode managed rate 54M
```Do you now have internet connectivity?

---

### Post by scrypt on 2009-03-28
I do indeed have wireless conectivity.

Good on ya Chili...

So thay are the commands fo me to use to have wireless connectivity, all be it untill I reboot..

I am more than happy with that.

Thank-you

---

### Post by chili555 on 2009-03-28
> **scrypt said:**
> I do indeed have wireless conectivity.

Good on ya Chili...

So thay are the commands fo me to use to have wireless connectivity, all be it untill I reboot..

I am more than happy with that.

Thank-youHappy to help. Enjoy!

---

### Post by scrypt on 2009-03-30
Hi Chili555

I have not added solved to this thread just yet because I wanted to make sure all was okay with all the commands etc etc???

All is okay and the commands you gave are fine.

But I have one more question?

With the commands you gave me to put my Card back into Managed mode.

I can put my card back into managed mode by using the commands:

sudo rmmod -f ipwraw
sudo modprobe iwl3945
sudo ifup wlan0 mode managed rate 54M

But. I can actually put my card into Managed mode using the first two of the three commands.

Can you let me know what the third command is : sudo ifup wlan0 mode managed rate 54M

And also what it does?

Thank's

I will finish of this thread as solved once I learn about that last command!!

---

### Post by chili555 on 2009-03-30
> sudo ifup wlan0 mode managed rate 54M
Oops! You got me there! You are getting pretty experienced.

Sorry, it should have been as follows:```
sudo ifup wlan0
sudo iwconfig wlan0 mode managed rate 54M
```That means, 'please bring up my interface wlan0, and then, since it's a wireless interface, set it's mode to managed and at a bit rate as high as possible, up to 54 Mb/s.'

Sorry for my error.

---

### Post by scrypt on 2009-04-01
Hi ya Chili.

All was working fine with the commands you gave me to put my card back into Managed mode to surf the net.

BUT. I have decided to hide my SSID. 

and I No longer can surf the net wirelessly by removing ipwraw and reloading iwl3945.

How can I rectify this?

I have had a god look into it, but I cannot find a solution?

Thank's

---

### Post by scrypt on 2009-04-01
No problem about the error

---

### Post by scrypt on 2009-04-01
Chili...

Sry. I was not entering correct name of my router in "connect to a hidden wireless Network". Network configuration settings.

I do still have on problemo though.

I have created a couple of wrong hidden wireless network connections, whilst trying to correctly configure my own?

How do I delete these?

They do not appear in edit connections?

any suggestions Chili??

Also are there seems to be a couple of pages missing from this thread. Originally where where 7. but now there are only 5?

Do you know anything about this??

scrypt

---

### Post by chili555 on 2009-04-01
> How do I delete these?

They do not appear in edit connections?Are you using Network Manager or manual configuration? I know nothing about NM except it doesn't work well for me.> Also are there seems to be a couple of pages missing from this thread. Originally where where 7. but now there are only 5?

Do you know anything about this??Not a thing. I am not a forum moderator, nor have I ever been in contact with one.

---

### Post by scrypt on 2009-04-01
Once agin Chili. False alarm.

I could not see the first page properly because of these silly april fools day colour changes.

NOT FUNNY UBUNTU...


oh.. im using network manager.

What do you use to configure your network??

---

### Post by chili555 on 2009-04-01
> What do you use to configure your network??I use the terminal to edit */etc/network/interfaces.* Since none, but one, of my computers ever leave home, I really don't have any need to select from several networks. I just need to reliably connect to mine!

I would guess there is, somewhere, a networkmanager.conf file, or something similar, that you could locate that has persistent settings stored in it. If you can find it, you ought to be able to remove the settings you no longer need.

Since I don't have it, I can't even guess where it is.

---

### Post by scrypt on 2009-04-03
Hi Chili.

I have got my card running perfectly with the commands you gave me. so thanks for that.

I am learning about my own networks WPA-PSK protected network

I am using aircrack-ng to test it.

I can get upto where i need to add a wordlist/dictionary to my command so aircrack can run a brute-force attack on the found.

this is the command :

sudo aircrack-ng -w password.lst -b 00:00:00:00:00:00 psk*.cap

The purpose of this step is to actually crack the WPA/WPA2 pre-shared key. To do this, you need a dictionary of words as input. Basically, aircrack-ng takes each word and tests to see if this is in fact the pre-shared key. 

do you know how i can add a wordlist or dictionary to the command for aircrack to try??

---

### Post by chili555 on 2009-04-03
I am very sorry, my friend, I know nothing about aircrack.

---

### Post by scrypt on 2009-04-03
Okay mate no worries.

But i have now downloaded a password list to my desktop
and i need to add it to my command so aircrack can check against it.

here is an example of the command:

 sudo aircrack-ng -w password.lst -b 00:00:00:00:00:00 psk*.cap

i nned to add my created password list to the command by entering the full path to my password list.

can you show me how to do this please chili, seeing as your clued up to this??

---

### Post by chili555 on 2009-04-04
I know nothing about aircrack. However, if you want to give a command the full path to a file, it would be about like this:```
~/Desktop/password.lst
```This assumes the file is currently on your desktop. The symbol ~ is accepted equivalent for /home/username. Of course, give the command the actual name of the list if it's not *password.lst.*
I would actually think that if your terminal is in the directory where the list is located, that an absolute path would not be needed.

---

### Post by scrypt on 2009-04-04
Thank's Chili.

Im not above admiting that I don't get it??

I have tried this :

 sudo aircrack-ng -w /home/mark/Desktop/wpa.txt -b 00:00:00:00:00:00 psk*.cap

And this :

 sudo aircrack-ng -w ~/Desktop/wpa.txt -b 00:00:00:00:00:00  psk*.cap

But it's just not having any of it? I have searched hard for an answer. with no luck.

All I get is this no matter what I do:

Opening psk-14.cap
Opening psk-15.cap
Opening psk-16.cap
Opening psk-17.cap
Opening psk-18.cap
Opening psk-19.cap
Opening psk-20.cap
Opening psk-21.cap
Opening psk-22.cap

Invalid packet capture length 0 - corrupted file?

Can you see where I'm going wrong?
It's driving me near bonkers :)

---

### Post by scrypt on 2009-04-04
Chili..

when I use the commands you gave me to put my card into Monitor Mode.
My system completely freezes.
Even if I turn Off my wireless card.

These are the commands you gave me:-

To go back to monitor mode is simply the reverse:
Code: Or Re-Boot. to automatically get monitor wifi0 mode

sudo ifdown wifi0
sudo rmmod -f iwl3945
sudo modprobe ipwraw

What can i do to stop my sytem freezing, where am i going wrong??

---

