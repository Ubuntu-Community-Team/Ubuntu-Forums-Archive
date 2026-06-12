---
title: "Dell D620 Wireless problems"
date: 2012-01-27
forum: Networking &amp; Wireless
---

### Post by Chasmo on 2012-01-27
I bought a never used dell latitude D620 over the internet. I saw a date of 2008 when  I booted it up. It had windows 7 on it. I wiped it with a disk of ubuntu 11.10. I am having No luck getting the wireless to work. I have clicked the enable wireless and done all that I know to get it to work. no luck. any help is welcome. Thanks C

---

### Post by Kixtosh on 2012-01-28
Have you found this thread yet, on the same topic?

[http://ubuntuforums.org/showthread.php?t=1491147](http://ubuntuforums.org/showthread.php?t=1491147)

If it doesn't help, try these directions so that you can be helped better:

[http://ubuntuforums.org/showthread.php?p=6183681](http://ubuntuforums.org/showthread.php?p=6183681)

---

### Post by Rodney9 on 2012-01-28
This link may help - [https://answers.launchpad.net/ubuntu/+question/12444](https://answers.launchpad.net/ubuntu/+question/12444)

Hints from above 

Open a terminal and type

lspci

look for the wireless chipset/

Check for additional restricted drivers.

Google "dell latitude D620 Ubuntu"


Rodney

---

### Post by Chasmo on 2012-01-28
Thanks for all the help. I have tried your suggestions to no avail
I ran the ls and found I have a broadcom BCM 4311 802 11 b/g wlan rev 1. 
The problem seems to be that the card wont turn on. I went to the bios and made sure the wireless is enabled and the switch was on. I installed wicd and removed gnome wireless manager. rebooted and still the card wont come on. I followed the link to the dell site to download a driver that may work but they require windows explorer to use their site. (can you believe that!)
Any ideas?

---

### Post by bkratz on 2012-01-28
> **Chasmo said:**
> Thanks for all the help. I have tried your suggestions to no avail
I ran the ls and found I have a broadcom BCM 4311 802 11 b/g wlan rev 1. 
The problem seems to be that the card wont turn on. I went to the bios and made sure the wireless is enabled and the switch was on. I installed wicd and removed gnome wireless manager. rebooted and still the card wont come on. I followed the link to the dell site to download a driver that may work but they require windows explorer to use their site. (can you believe that!)
Any ideas?

This will give you what you need for either 11.04 or 11.10. We may still have to have a look at rfkill list all to see if there is some hardblock issue though.

---

### Post by Chasmo on 2012-01-28
> **bkratz said:**
> This will give you what you need for either 11.04 or 11.10. We may still have to have a look at rfkill list all to see if there is some hardblock issue though.

did I miss something?

---

### Post by Kixtosh on 2012-01-28
> **Chasmo said:**
> ... I ran the ls and found I have a broadcom BCM 4311 802 11 b/g wlan rev 1.  ...Isn't that "one of them cards from hell"?!

There seems to be a driver from Broadcom for it:

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

This thread is on the same topic, and it's recent, and it's marked as solved. It might be worth reading:

[http://ubuntuforums.org/showthread.php?t=1870390&highlight=BCM+4311](http://ubuntuforums.org/showthread.php?t=1870390&highlight=BCM+4311)

---

### Post by Chasmo on 2012-01-28
I found a link on google here in the forum that had a solution. There is a driver in the ubuntu depository I copy and pasted the driver name in the software center found and installed the driver rebooted. still no wireless networks found.. Now I cant find the link where I got the info. ugg

---

### Post by bkratz on 2012-01-28
> **Chasmo said:**
> I found a link on google here in the forum that had a solution. There is a driver in the ubuntu depository I copy and pasted the driver name in the software center found and installed the driver rebooted. still no wireless networks found.. Now I cant find the link where I got the info. ugg

Looks like I forgot the link, sorry?  Glad you got it sorted out though. Here is the missing link!!!!

[https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04](https://help.ubuntu.com/community/WifiDocs/Device/Broadcom_BCM4311_Natty_11.04)

See this address

---

### Post by mörgæs on 2012-01-28
Moved to the wireless forum.

---

### Post by Kixtosh on 2012-01-28
There are dozens of threads about these Broadcom wireless issues, but many of them have been solved.

Have you tried this command in Terminal?

```
sudo apt-get install firmware-b43-installer
```There also seem to be issues that may require blacklisting, and other issues that prevent the card from starting up at boot, but it might help others to help you if you would paste the output of some of the commands from the link I gave you earlier about how to report wireless problems. Please do this as code (using the # icon in the reply window) to make it more readable!

P.S. This thread is also specifically about your issue: [http://ubuntuforums.org/showthread.php?t=1604868&highlight=restricted+drivers](http://ubuntuforums.org/showthread.php?t=1604868&highlight=restricted+drivers)

It can be tedious wading through threads, but for your card, which seems quite common in Dell laptops, it is almost certain that the solution has already been identified dozens of times.

---

### Post by Chasmo on 2012-01-28
here is the latest thing I have tried.

---

### Post by Chasmo on 2012-01-28
I did what the link recomended and copy pasted commands in the terminal installed and removed Still no luck. I wonder if there is a way to test to see if the card works at all?

---

### Post by Chasmo on 2012-01-28
This is the output for lspci.

---

### Post by Chasmo on 2012-01-28
here are a couple of screen shots

---

### Post by Chasmo on 2012-01-28
I dont know why my screen shots are not showing

---

### Post by Chasmo on 2012-01-28
> **Kixtosh said:**
> There are dozens of threads about these Broadcom wireless issues, but many of them have been solved.

Have you tried this command in Terminal?

```
sudo apt-get install firmware-b43-installer
```There also seem to be issues that may require blacklisting, and other issues that prevent the card from starting up at boot, but it might help others to help you if you would paste the output of some of the commands from the link I gave you earlier about how to report wireless problems. Please do this as code (using the # icon in the reply window) to make it more readable!

P.S. This thread is also specifically about your issue: [http://ubuntuforums.org/showthread.php?t=1604868&highlight=restricted+drivers](http://ubuntuforums.org/showthread.php?t=1604868&highlight=restricted+drivers)

It can be tedious wading through threads, but for your card, which seems quite common in Dell laptops, it is almost certain that the solution has already been identified dozens of times.

I have indeed tried this thread. so far I have checked to make sure wifi is enabled in the bios checked the wifi switch. I have downloaded recomended drivers using the ubuntu software center, I have used terminal to get and install drivers.I have removed drivers. I have used synaptic manager of which I posted a screen shot. Still not working. Is there a way to check the wifi card to see if it really works?

---

### Post by bkratz on 2012-01-28
could you copy/paste the output of 


ls /etc/modprobe.d

That was LS in lowercase

back here to see if the suspect blacklist files are in it


better command

cat /etc/modprobe.d/* | egrep 'b43|bcm|ssb|wl'

and to answer your question

sudo iwlist scan &#8211; shows wireless networks that are available in the area along with basic encryption information

---

### Post by Chasmo on 2012-01-28
no such file in the directory

---

### Post by Chasmo on 2012-01-28
I should be able to paste from the clip board hear right?

---

### Post by Chasmo on 2012-01-28
I am trying to add an attachment of a screen shot.

---

### Post by Chasmo on 2012-01-28
I took several screen shots that were recomended. Here is another.

---

### Post by Chasmo on 2012-01-28
this may be more info than you want.

---

### Post by kevdog on 2012-01-28
Your using the b43 chipset as I suspected.  

I'd just post copy and paste and avoid taking screen shots.

Bring the wireless card up manually (this is for testing not everyday use).
This is assuming there is no encryption on the router 

sudo ifconfig eth0 down
sudo dhclient -r eth0
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid "ESSID_IN_QUOTES"
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0 &

Then recheck ifconfig to see if you have a ip address.

If you need to fire back up the wired eth0 connection (since you brought it down, do the following):
sudo ifconfig wlan0 down
sudo ifconfig eth0 up
sudo dhclient eth0 &


sudo iwlist wlan0 scan
This command above should scan your network to see if you can see your router!!

Try avoid screenshots please! Just copy and paster from the terminal window to here please.

---

### Post by Chasmo on 2012-01-28
here is the rest of it.

---

### Post by Chasmo on 2012-01-28
sorry to sound stupid but how do I check to see if I have an IP address?

---

### Post by Chasmo on 2012-01-28
I do have a password for the router.

---

### Post by Chasmo on 2012-01-28
WooHoo I have a wifi light on first time.

---

### Post by Chasmo on 2012-01-28
screen shot

---

### Post by Chasmo on 2012-01-28
sorry about the screen shots.Just so I will know. why are screenshots a problem?

    inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:18:f3:6b:15:12  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:18:f3:6b:15:12  
          inet addr:169.254.4.238  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

[1]+  Done                    sudo dhclient wlan0
charlie@charlie-Latitude-D620:~$

---

### Post by kevdog on 2012-01-28
Ok -- you are getting somewhere.

If you would just copy and paste the terminal commands as you entered them, we could see the output of the various commands.

Also, when the wlan0 light is on, (and the eth0 device down), what do you get for:
sudo iwlist wlan0 scan

---

### Post by Kixtosh on 2012-01-28
> **Chasmo said:**
> sorry about the screen shots.Just so I will know. why are screenshots a problem? ...It's sort of forum etiquette. They're harder to read and cannot be partially quoted.

When you copy and paste output from the terminal, or show commands, you should "wrap" the text you have pasted into the reply window as "code" ... by first selecting it with your mouse (or keyboard), and then, when the selected text is still highlighted, clicking the # icon in the reply window:
```
thus
```This also makes it much easier for those who want to help you to follow the text. It takes more effort to try to understand quoted output or commands buried in a sea of text when it's not wrapped as code.

Both of these suggestions are similar in the annoyance they provoke to reading posts made from mobile devices when the user doesn't either use capital letters at the start of sentences or punctuation.

---

### Post by Chasmo on 2012-01-28
sorry about all the screen shots I didn't know.

---

### Post by Chasmo on 2012-01-28
```

```                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD700050F204104A00011010440001021041000100103B00010310470010F7DCFCEBD4FCD18BC8B4280A17902DCA102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    IE: Unknown: DD090010180203F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00

[1]+  Done                    sudo dhclient wlan0
charlie@charlie-Latitude-D620:~$

---

### Post by kevdog on 2012-01-29
Ok -- you are getting somewhere.

Is your router running wpa2 security?

---

### Post by Chasmo on 2012-01-29
```

```

sudo] password for charlie: 
wlan0     Scan completed :
          Cell 01 - Address: 98:FC:11:8A:E1:D8
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"cosmo"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000012e7128a18a
                    Extra: Last beacon: 432ms ago
                    IE: Unknown: 0005636F736D6F
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030109
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1609001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD700050F204104A00011010440001021041000100103B00010310470010F7DCFCEBD4FCD18BC8B4280A17902DCA102100074C696E6B737973102300054531303030102400063132333435361042000234321054000800060050F2040001101100054531303030100800020084103C000101
                    IE: Unknown: DD090010180203F0040000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E00623charlie@charlie-Latitude-D620:~$

---

### Post by Chasmo on 2012-01-29
> **kevdog said:**
> Ok -- you are getting somewhere.

Is your router running wpa2 security?

I really don't know. I do have a password for it but I don't remember if it is wpa2 or not.

---

### Post by Chasmo on 2012-01-29
looking at the out put I would say that it is.

---

### Post by kevdog on 2012-01-29
Ok -- just for testing purposes we have a few options.

#1 -- Can you turn off the encryption on the router?  If you can we can confirm your network card is indeed working -- basically we've established a foundation to build from.

If not...
#2 We'll proceed on.  It seems like wpa2 to me.  

Do the following:
gksu gedit /etc/wpa_supplicant.conf

Within the file put the following:

ctrl_interface=/var/run/wpa_supplicant

network={
        ssid="ESSID_IN_QUOTES"
        psk="ASCII PSK Password in Quotes"
        key_mgmt=WPA-PSK
        proto=RSN WPA
        pairwise=CCMP TKIP
        group=CCMP TKIP
}

Save the file.

Now lets bring everything up by hand to see if this card works.  Later after establishing a foundation we can make it start automatically.

sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -B
sudo dhclient wlan0

You can check if you got an ip address issued from the router with ifconfig.

Let me know what happens.

---

### Post by Chasmo on 2012-02-18
I was called out of town for a while and have not been back to the forums for a while. I have solved my problem by buying an intel chipset from a supplier at amazon.com. I installed the intel chip and it hooked up as soon as I started my computer. Dell should be ashamed for using a supplier who does not support linux as they purport to be linux friendly. SOLVED.

---

