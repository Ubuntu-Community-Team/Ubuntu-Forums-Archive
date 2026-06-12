---
title: "Wifi won't connect on 13.04 with BCM 4313"
date: 2013-05-02
forum: Networking &amp; Wireless
---

### Post by bagelong on 2013-05-02
I have a Lenovo E530 with the BCM 4313 wireless controller.  I was running 12.10 and had no wifi issues after installing the additional driver (Broadcom 802.11 Linux STA wireless driver source from bcmwl-kernel-source).  After upgrading to 13.04 my wifi will no longer connect.  I tried purging and reinstalling the driver with no luck.  I have  searched pretty thoroughly and have not found a solution, although it looks like this is a 13.04 problem. Any help would be appreciated.  Thanks in advance.

---

### Post by Hadaka on 2013-05-02
hi, give this a read...
the varunendra fix.
[http://ubuntuforums.org/showthread.php?t=2140640&page=4&p=12629619#post12629619](http://ubuntuforums.org/showthread.php?t=2140640&page=4&p=12629619#post12629619)
*post #31

---

### Post by bagelong on 2013-05-02
I got through step 7 and all seemed to be going well, but something didn't go right when I began to put in the commands in the terminal for step 8.  Now, I no longer have any active wifi.  I am sorry for my noobness on this, but was I supposed to exit the directory before step 8, because I did not.  Also, at "cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless" I wasn't sure whether `uname -r` was supposed to be put into the command line or if I was supposed to insert something specific to my system there.

---

### Post by Hadaka on 2013-05-02
Hi, if you got the wl.ko file then you were fine.,
the 'uname -r' inserts your current kernel version
so that is correct...leave it as uname -r
doest sound like you messed anything up and
you could probably begin again at step 8 and be fine.
keep us posted.
thanks.

---

### Post by bagelong on 2013-05-02
Okay, I'll try again from scratch.

---

### Post by Hadaka on 2013-05-02
please verify your correct bit rate...32 or 64 so that
you download the needed file....to see what you have
please do..
```
arch
```
then..once you load the correct version
at step 8...just copy and paste the commands
to avoid possible typos
good luck.

---

### Post by bagelong on 2013-05-02
SUCCESS!!  I think I was just being impatient, and for some reason, the process took a little bit of time to complete behind the scenes.  I am not exactly sure what we just did, but whatever changes we made to the driver seem to have worked.  Thanks so much for your time.  Hope this will help some others as well.

---

### Post by Hadaka on 2013-05-02
Awesome ! glad it worked, i;m sure Varunendra will
be pleased as well.
take the time to mark this thread SOLVED
so it will help others.

---

### Post by varunendra on 2013-05-03
> **bagelong said:**
> SUCCESS!!  I think I was just being impatient, and for some reason, the process took a little bit of time to complete behind the scenes.
For the driver building process and the update of initramfs, 2-4 minutes are normal depending on system configuration. Could be more on slower systems, but the main thing to notice is messages on the screen. Warnings can usually be safely ignored, but 'Errors' are something that should be reported back.

> **Hadaka said:**
> Awesome ! glad it worked, i;m sure Varunendra will
be pleased as well.
No doubt it raised my BP, because the solution is still experimental for me. As such, I'd be very pleased if it proved to be both stable and performing nicely.

@bagelong,
Thanks for the feedback! However, it'll be really helpful for us and many more possibly following the solution if you could keep the wireless on test-bed for a couple of days, then post back if it proved to be stable. Of course post back immediately if you face any more problems. We are ready to dig more if required, although I wish we don't have to.

---

### Post by bagelong on 2013-05-03
A couple of things came up when I put the string of commands into the terminal.  I did the whole process three times (steps 1-8), so I finally got pretty proficient at it.  Each time, at step 8, when I copied and pasted the whole block of commands, I got a message that my password was incorrect at the "sudo su" step, even though I know it was correct.  When I put the password in again, it was accepted and would progress past this step.  I thought the process was stopping a few times, so I would repeat the last command.   In retrospect, I think it was just taking longer than I thought it would.  For some reason, it seemed to hang the longest at the "exit" step.  At one point, I repeatedly tried to exit the terminal, thinking I was done, and I got the message that a process was still running in the terminal.  Anyway, I think the moral to the story is to be patient, and let the process complete.

---

### Post by varunendra on 2013-05-03
> **bagelong said:**
> ...Each time, at step 8, when I copied and pasted the whole block of commands, I got a message that my password was incorrect at the "sudo su" step,
From what I get from your description, you were copy-pasting all the commands in step 8 at once, so 'sudo su' considered the following characters (maybe the newline) as your password, which was obviously wrong. Correct way (always)-
One command at a time > let it finish > next command.

I'll modify my original post to avoid the confusion..

> **bagelong said:**
> Anyway, I think the moral to the story is to be patient, and let the process complete.
Correct!! :)

---

### Post by bagelong on 2013-05-13
A day or two after Wifi was up and running again with the fix from varunendra, I had to do a restart and lost wifi again.  I went back through the fix and it worked like a charm again.  Everything went well (no restarts) until last night when the computer was left unplugged.  Upon restart this morning, wifi was down again.  I have repeated this fix several times with no luck this time.  Any suggestions?

---

### Post by Hadaka on 2013-05-13
Hi Bagelong, try this to keep the setting..
please COPY and paste the following...

```
echo "wl" | sudo tee -a /etc/modules
```

this will load the driver on boot or on power up.
thanks.

---

### Post by bagelong on 2013-05-13
The problem is that I don't have working wifi, so I am not sure there is a setting to keep now.

---

### Post by Hadaka on 2013-05-14
Hi, all the files you built should still be there.
please do...

```
sudo modprobe wl
```

  your wireless should be alive now

*If YES then do the command in post 13

---

### Post by bagelong on 2013-05-14
I went through all of the steps several times this evening with no results.  This included deleting all of the previously downloaded, extracted, and modified files (basically trying to undo steps 1-7), then restarting the whole process. I checked each time and the "wk.lo" file was present in the extracted directory, then I proceeded onto step 8.  Still, no luck.  Finally, I reinstalled the Broadcom driver (trying to recreate my original scenario when I upgraded from 12.10 to 13.04), then started with step 1 again, and it finally worked.  The only reason I tried this was because at the "apt-get purge bcmwl-kernel-source" there was nothing to purge, so I thought having the driver present might be necessary for some reason.  Not sure if this helps, but I am now up and running again.  

After getting the wifi back, I did run the command in step #13, so hopefully, I won't have to repeat this again with the next reboot.   

Thanks so much for all of your help on the matter.  I guess sometimes it just takes a little trial and error.

By the way, can I delete the extracted directory from my desktop at this point?

---

### Post by Hadaka on 2013-05-14
Glad you got it working again, did you put the
code,,,
```
echo "wl | sudo tee -a /etc/modules 
```
in?
*if not..please do that.(sorry..i see you did do that..thanks)
yes you can delete the files, you should keep the original
downloaded file in your Download folder for possible future use.
if you are satisfied with everything,please mark this solved.
thanks.

how to -> [URL="https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads"]https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads

ps.Thanks! you did great with everything !!!!
[/URL]

---

### Post by bagelong on 2013-05-14
Yes, I did enter the code from above in a terminal.  Any idea why the fix only worked after reinstalling the Broadcom driver?

p.s.  Still connecting after a quick reboot.  Thanks again to you and varunendra for your help and the addition of the step in post #13 above.

---

### Post by varunendra on 2013-05-14
Glad you and hadaka worked it out again. However -
> **bagelong said:**
> I went through all of the steps several times this evening with no results.
You shouldn't have needed that unless there was a kernel upgrade. In case of a kernel upgrade it was expected, otherwise it is something we need to figure out why it happened.

Accordingly, please post -
```
uname -mr
dpkg -s bcmwl-kernel-source | grep -i version
```
..to show us the kernel and the driver versions currently in use.

> The only reason I tried this was because at the "apt-get purge bcmwl-kernel-source" there was nothing to purge, so I thought having the driver present might be necessary for some reason.  Not sure if this helps, but I am now up and running again.
The "apt-get purge.." part isn't necessary if you are sure the other version does not exist. Although it doesn't hurt even if the packages are already non-existent. It does nothing more than purging the desired package(s) along with any configuration files it might have created. You shouldn't need to install the default version to make the solution work. So the fact that it worked after doing so has me confused. May be the output of the above commands could possibly shed some light on it.

> By the way, can I delete the extracted directory from my desktop at this point?
Just what hadaka said :)

I am really pleased that you got it working, I just wish I knew what went wrong in-between.

---

### Post by bagelong on 2013-05-14
```

long@long-Lenovo:~$ uname -mr
3.8.0-19-generic i686
long@long-Lenovo:~$ dpkg -s bcmwl-kernel-source | grep -i version
dpkg-query: package 'bcmwl-kernel-source' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

```

---

### Post by bagelong on 2013-05-14
I've retraced my steps some, and I have come to the conclusion that I have actually been having two wifi problems, but I have been treating them as one.  

Problem #1 - first demonstrated when I upgraded from 12.10 - 13.04.  My home wifi network would show in the available network lists, but I could not connect to it (i.e., continual attempt at connection showing in the indicator, but never able to make the connection).  This problem was solved when I correctly applied Varunendra's fix. 

Problem #2 - The first time I rebooted after successfully applying Varunendra's fix, my wifi indicator showed that I was weakly connected to my network, but I could not access the internet - web pages would never load and would eventually time out.  I tried reapplying Varunendra's fix at these times with no improvement.  At that time I tried some other fixes, which included reinstalling and updating the Broadcom driver.  This recreated problem #1.  I then applied Varunendra's fix and wifi was up and running again.  I essentially went back through this same process again yesterday after my computer was left unplugged and I had to reboot.  

I have since applied the recommended fix at post #13 above and I did reboot with no loss of Wifi.  Not sure if any of this will help you guys.  Thanks again, so much, for all of your help.  If I can provide any further information let me know.

---

### Post by varunendra on 2013-05-15
> **bagelong said:**
> If I can provide any further information let me know.
Yes you can help us more.

First - a personal favour to me - please stop calling that "Varunendra's fix", both of you. Its embrrassing as it is mostly a 'stolen fix', I've only put it together in one place. :P

Second - this was unexpected, although it may be because we copied the wl driver manually -
> ```
long@long-Lenovo:~$ dpkg -s bcmwl-kernel-source | grep -i version
dpkg-query: [COLOR="#FF0000"]package 'bcmwl-kernel-source' is not installed and no information is available[/COLOR]
```
So please post instead -
```
modinfo wl
```

Third, regarding the 'weak connection' issue, please post -
```
iwconfig
ifconfig
```
Maybe we can see and suggest something that makes it possibly better. Additionally, you may wish to post a complete diagnostics report (iwconfig is included in it) following the "Wireless Script" link in my signature. But that's not required if things are satisfactory.

---

### Post by bagelong on 2013-05-15
#1  How about I refer to it as VSF (Varunendra's Stolen Fix)?

#2
```

long@long-Lenovo:~$ modinfo wl
filename:       /lib/modules/3.8.0-19-generic/kernel/drivers/net/wireless/wl.ko
srcversion:     49E2D90EE4D6877632DEDB0
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000435Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A99Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        lib80211
vermagic:       3.8.0-19-generic SMP mod_unload modversions 686 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           name:string

```

#3  My connection speed is fine now because of the most recent use of VSF after reinstall of the Broadcom drivers, but here is the requested output.
```

long@long-Lenovo:~$ iwconfig
eth7      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:218  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

lo        no wireless extensions.

eth6      no wireless extensions.

long@long-Lenovo:~$ ifconfig
eth6      Link encap:Ethernet  HWaddr b8:88:e3:35:57:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth7      Link encap:Ethernet  HWaddr 74:e5:43:17:93:09  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76e5:43ff:fe17:9309/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:229152 errors:0 dropped:0 overruns:0 frame:5755239
          TX packets:172625 errors:18 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:228120835 (228.1 MB)  TX bytes:30941641 (30.9 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10448 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10448 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1624730 (1.6 MB)  TX bytes:1624730 (1.6 MB)

```

---

### Post by varunendra on 2013-05-15
> **bagelong said:**
> #1  How about I refer to it as VSF
You guys are determined :evil:

The output of modinfo is as expected, but this looks cryptic, none like I have ever seen so far -
> **bagelong said:**
> ```

long@long-Lenovo:~$ iwconfig
eth7      IEEE 802.11  Access Point: **[COLOR="#FF0000"]Not-Associated[/COLOR]**   
          **Link Quality:5**  Signal level:218  **Noise level:164**
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

```
The highlighted part above doesn't seem good to me. Are you too far from the access point? Although since it is cryptic, I may be misinterpreting it. But if it is what it looks like, then the noise level is too high than 'tolerable'. Usually it should be under 65. But I don't know if it is in normal units. Similarly, the link quality is normally displayed in the form of "something1/something2" which is interpreted as "something1 out of something2". Now I can't say that "5" is on what scale :-k

[COLOR="#800000"]**EDIT :** Noticed later, it shows both "**not associated**" as well as link quality and other stuff - which only appears when it IS associated with an access point. So this is really a messed up output. I'd have to find more examples, or seek advice from my seniors to get an idea of what is going on here[/COLOR] :P

So for now, since I'm not even sure I'm interpreting it correctly, let's leave it as long as the connection is fine.

Finally -
> **bagelong said:**
> ```

long@long-Lenovo:~$ ifconfig
..
..
eth7      Link encap:Ethernet  HWaddr 74:e5:43:17:93:09  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          **inet6 addr: fe80::76e5:43ff:fe17:9309/64 Scope:Link**
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:229152 errors:0 dropped:0 overruns:0 frame:5755239
          TX packets:172625 **[COLOR="#FF0000"]errors:18[/COLOR]** dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:228120835 (228.1 MB)  TX bytes:30941641 (30.9 MB)
          Interrupt:17 

```
Usually I recommend to disable IPv6 altogether (using [this]("http://ubuntuforums.org/showthread.php?t=2143561&p=12640479#post12640479") method), but that doesn't explain the 'error packets'. Besides, as long as it is working, just :-\"

We'd be right here if needed :)

---

### Post by bagelong on 2013-05-19
Okay, I now think I am back to problem two.  I still have a connection, but it is not very good.  I am probably about 7 feet from my router, but the indicator shows a weak connection and web page loading is hit or miss.  This is a big change from a few days ago when I first reapplied the fix.

---

### Post by varunendra on 2013-05-19
> **bagelong said:**
> Okay, I now think I am back to problem two.  I still have a connection, but it is not very good.  I am probably about 7 feet from my router, but the indicator shows a weak connection and web page loading is hit or miss.  This is a big change from a few days ago when I first reapplied the fix.
Hmm..
While you are connected via wireless, please post outputs of -
```
iwconfig
ifconfig
sudo iwlist scan
dmesg | grep wl
```

Let's see if something obvious jumps out.

---

### Post by bagelong on 2013-05-20
```

long@long-Lenovo:~$ iwconfig
wlan3     IEEE 802.11bgn  ESSID:"Cisco47799"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:6D:8F:90:E0:23   
          Bit Rate=43.3 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10428  Invalid misc:2214   Missed beacon:0

lo        no wireless extensions.

eth6      no wireless extensions.

long@long-Lenovo:~$ ifconfig
eth6      Link encap:Ethernet  HWaddr b8:88:e3:35:57:7b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:10525 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10525 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1429279 (1.4 MB)  TX bytes:1429279 (1.4 MB)

wlan3     Link encap:Ethernet  HWaddr 74:e5:43:17:93:09  
          inet addr:192.168.1.120  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::76e5:43ff:fe17:9309/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:139374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:96592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:96998536 (96.9 MB)  TX bytes:16467888 (16.4 MB)

long@long-Lenovo:~$ sudo iwlist scan
[sudo] password for long: 
wlan3     Scan completed :
          Cell 01 - Address: 58:6D:8F:90:E0:23
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"Cisco47799"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000118e9445b4
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 000A436973636F3437373939
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010B4BDE38EDD78AAD1B25D93F1902999EE10210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30321042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800020084103C000103
                    IE: Unknown: DD090010180204F0040000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: 58:6D:8F:90:E0:25
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"Cisco47799-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000118e945b68
                    Extra: Last beacon: 52ms ago
                    IE: Unknown: 0010436973636F34373739392D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606001700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180204F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

lo        Interface doesn't support scanning.

eth6      Interface doesn't support scanning.

long@long-Lenovo:~$ dmesg | grep wl
[   26.826118] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[   26.826376] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[   28.887873] wlan3: authenticate with 58:6d:8f:90:e0:23
[   28.897635] wlan3: send auth to 58:6d:8f:90:e0:23 (try 1/3)
[   28.899124] wlan3: authenticated
[   28.899406] wlan3: associate with 58:6d:8f:90:e0:23 (try 1/3)
[   28.902604] wlan3: RX AssocResp from 58:6d:8f:90:e0:23 (capab=0x411 status=0 aid=3)
[   28.903342] wlan3: associated
[   28.903347] IPv6: ADDRCONF(NETDEV_CHANGE): wlan3: link becomes ready
[16835.223378] wlan3: authenticate with 58:6d:8f:90:e0:23
[16835.224396] wlan3: send auth to 58:6d:8f:90:e0:23 (try 1/3)
[16835.425688] wlan3: send auth to 58:6d:8f:90:e0:23 (try 2/3)
[16835.629462] wlan3: send auth to 58:6d:8f:90:e0:23 (try 3/3)
[16835.833160] wlan3: authentication with 58:6d:8f:90:e0:23 timed out
[16849.485270] IPv6: ADDRCONF(NETDEV_UP): wlan3: link is not ready
[16877.959809] wlan3: authenticate with 58:6d:8f:90:e0:23
[16877.963366] wlan3: send auth to 58:6d:8f:90:e0:23 (try 1/3)
[16877.964886] wlan3: authenticated
[16877.966721] wlan3: associate with 58:6d:8f:90:e0:23 (try 1/3)
[16877.970123] wlan3: RX AssocResp from 58:6d:8f:90:e0:23 (capab=0x411 status=0 aid=3)
[16877.970850] wlan3: associated
[16877.970867] IPv6: ADDRCONF(NETDEV_CHANGE): wlan3: link becomes ready
[17739.073173] wlan3: deauthenticating from 58:6d:8f:90:e0:23 by local choice (reason=3)
[17740.045763] wlan3: authenticate with 58:6d:8f:90:e0:23
[17740.046971] wlan3: send auth to 58:6d:8f:90:e0:23 (try 1/3)
[17740.048557] wlan3: authenticated
[17740.052498] wlan3: associate with 58:6d:8f:90:e0:23 (try 1/3)
[17740.055762] wlan3: RX AssocResp from 58:6d:8f:90:e0:23 (capab=0x411 status=0 aid=3)
[17740.056905] wlan3: associated
long@long-Lenovo:~$ 

```

---

### Post by varunendra on 2013-05-20
> **bagelong said:**
> ```

long@long-Lenovo:~$ iwconfig
wlan3     IEEE 802.11bgn  ESSID:"Cisco47799"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 58:6D:8F:90:E0:23   
          Bit Rate=43.3 Mb/s   Tx-Power=19 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=29/70  Signal level=-81 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:10428  Invalid misc:2214   Missed beacon:0

```

Hmm.. that output is more familiar.. but, "wlan3"???? The "wl" driver assigns the interface name of "eth**x**" pattern, not "wlan**x**".
Looks like you are back on the native brcmsmac driver, probably due to a kernel upgrade? Let us take a look at -
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
```

---

### Post by bagelong on 2013-05-20
```

long@long-Lenovo:~$ uname -mr
3.8.0-21-generic i686
long@long-Lenovo:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0608]
	Kernel driver in use: bcma-pci-bridge
0c:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
	Subsystem: Lenovo Device [17aa:5000]
	Kernel driver in use: r8169
long@long-Lenovo:~$ lsmod
Module                  Size  Used by
parport_pc             27504  0 
bnep                   17669  2 
rfcomm                 37420  0 
ppdev                  12817  0 
snd_hda_codec_hdmi     36185  1 
coretemp               13131  0 
joydev                 17097  0 
snd_hda_codec_conexant    52256  1 
arc4                   12543  2 
kvm                   376505  0 
aesni_intel            18156  1 
aes_i586               16995  1 aesni_intel
xts                    12749  1 aesni_intel
lrw                    13057  1 aesni_intel
gf128mul               14503  2 lrw,xts
brcmsmac              521468  0 
thinkpad_acpi          69384  0 
nvram                  13986  1 thinkpad_acpi
ablk_helper            13357  1 aesni_intel
snd_hda_intel          38307  3 
cordic                 12518  1 brcmsmac
brcmutil               14355  1 brcmsmac
snd_hda_codec         117580  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
mac80211              526519  1 brcmsmac
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
uvcvideo               71279  0 
videobuf2_vmalloc      12920  1 uvcvideo
videobuf2_memops       13042  1 videobuf2_vmalloc
cryptd                 15613  1 ablk_helper
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
btusb                  17986  0 
snd_seq_midi           13132  0 
videobuf2_core         39161  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              436177  2 brcmsmac,mac80211
i915                  535507  3 
bluetooth             202069  11 bnep,btusb,rfcomm
snd_rawmidi            25114  1 snd_seq_midi
videodev               95806  2 uvcvideo,videobuf2_core
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
rtsx_pci_ms            12875  0 
snd_timer              24411  2 snd_pcm,snd_seq
drm_kms_helper         47545  1 i915
drm                   228750  4 i915,drm_kms_helper
snd                    56485  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
psmouse                81038  0 
bcma                   39645  1 brcmsmac
i2c_algo_bit           13197  1 i915
memstick               15842  1 rtsx_pci_ms
lp                     13299  0 
serio_raw              13031  0 
microcode              18286  0 
video                  18894  1 i915
parport                40753  3 lp,ppdev,parport_pc
soundcore              12600  1 snd
wmi                    18590  0 
lpc_ich                16925  0 
mei                    36197  0 
mac_hid                13037  0 
rtsx_pci_sdmmc         17238  0 
ahci                   25507  2 
libahci                26108  1 ahci
r8169                  61531  0 
rtsx_pci               32018  2 rtsx_pci_ms,rtsx_pci_sdmmc

```

---

### Post by varunendra on 2013-05-20
> **bagelong said:**
> ```

long@long-Lenovo:~$ uname -mr
3.8.0-**[COLOR="#FF0000"]21[/COLOR]**-generic i686
long@long-Lenovo:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0608]
	Kernel driver in use: **[COLOR="#FF0000"]bcma-pci-bridge[/COLOR]**

```

Indeed what I suspected. Please compile and install the wl driver again like you did previously. Plus this additional step to prevent the brcmsmac driver from loading :
```
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Reboot if necessary, and post back if our old driver gives you better speeds.

**PS:**
I know this is annoying to manually compile and install the driver again after each kernel upgrade. This can be automated as far as I know, using 'dkms', but unfortunately, I don't yet know how to use it. Thanks to my laziness :(

---

### Post by bagelong on 2013-05-20
I am not sure why I am getting this message.

```

root@long-Lenovo:/home/long/Desktop/hybrid-portsrc_x86_32-v5_100_82_112# modprobe -rfv wl
[COLOR="#FF0000"]FATAL: Module wl not found.[/COLOR]

```

---

### Post by Hadaka on 2013-05-20
Hi, you are getting that error..because the module isnt there any longer..
you will get the error on these 2 lines...
```

modprobe -rfv wl
sudo apt-get purge bcmwl-kernel-source
```
do both anyway..ignore the error...and continue on...all is well

---

### Post by bagelong on 2013-05-21
```

root@long-Lenovo:/home/long/Desktop/hybrid-portsrc_x86_32-v5_100_82_112# modprobe -v wl
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'brcmsmac'

```

---

### Post by varunendra on 2013-05-21
> **Hadaka said:**
> do both anyway..ignore the error...and continue on...all is well
Yup, he's absolutely correct. Thanks Hadaka!

Plus - I messed up the blacklist command earlier (the **echo "brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf** command). I have corrected that in the original post, it will be -
```
echo "**[COLOR="#0000CD"]blacklist[/COLOR]** brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```

To check if you already used the wrong command (although it won't hurt), please post -
```
cat /etc/modprobe.d/blacklist.conf
```

---

### Post by bagelong on 2013-05-21
After this "update-initramfs -u" I get the following string about 50 times
```

libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'brcmsmac'

```

I have gone through the fix 3-4 times and it happened the last two times

---

### Post by bagelong on 2013-05-21
```

long@long-Lenovo:~$ cat /etc/modprobe.d/blacklist.conf
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

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
brcmsmac

```

---

### Post by varunendra on 2013-05-21
> **bagelong said:**
> ```

libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'brcmsmac'

```
Evidently, I responded 1 minute late :D. Please read my previous post.

Although this error doesn't hurt, let's fix it. The easiest way -
```
sudo sed -i '/^brcmsmac/ d' /etc/modprobe.d/blacklist.conf
```

It doesn't matter whether you run this command before or after running the corrected one, it will just delete the incorrect line, thus fixing those error messages.


**EDIT:** Whew..!! Looks like we're in a race of responding to each-other.... You Win!! :P

---

### Post by bagelong on 2013-05-21
> **varunendra said:**
> Evidently, I responded 1 minute late :D. Please read my previous post.

Although this error doesn't hurt, let's fix it. The easiest way -
```
sudo sed -i '/^brcmsmac/ d' /etc/modprobe.d/blacklist.conf
```

It doesn't matter whether you run this command before or after running the corrected one, it will just delete the incorrect line, thus fixing those error messages.


**EDIT:** Whew..!! Looks like we're in a race of responding to each-other.... You Win!! :P

I ran this command

```
sudo sed -i '/^brcmsmac/ d' /etc/modprobe.d/blacklist.conf
```

then started back at step 6.  I still got this when I input this command

```

root@long-Lenovo:/home/long/Desktop/hybrid-portsrc_x86_32-v5_100_82_112# modprobe -v wl
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/blacklist.conf line 56: ignoring bad line starting with 'brcmsmac'

```

---

### Post by varunendra on 2013-05-21
Hmm.. shouldn't happen. Let's take another look at the blacklist.conf file. Please post -
```
cat /etc/modprobe.d/blacklist.conf | tail -4
```
The "tail" part is to just show the last 4 lines, as that's what we are interested in.

And you don't need to build the module everytime. Once it is built for the current kernel, just proceed with step 8.

---

### Post by bagelong on 2013-05-21
responding from my phone, as wifi is now absent.  I can get on with Ethernet if needed.

---

### Post by Hadaka on 2013-05-21
yes ethernet

---

### Post by bagelong on 2013-05-21
Ethernet is available.  I suspect you will want some output.  Lay it on me.

---

### Post by Hadaka on 2013-05-21
```

cat /etc/modprobe.d/blacklist.conf | tail -4
```

---

### Post by varunendra on 2013-05-21
```
cat /etc/modprobe.d/blacklist.conf | tail -4
modinfo wl
```
post these via ethernet or whatever..

---

### Post by bagelong on 2013-05-21
```

long@long-Lenovo:~$ cat /etc/modprobe.d/blacklist.conf | tail -4
# really needed.
blacklist amd76x_edac
blacklist brcmsmac
blacklist brcmsmac

```

I think I got that corrected.  Don't remember running the corrected code twice.  Does it matter that it is repeated?

---

### Post by bagelong on 2013-05-21
```

long@long-Lenovo:~$ modinfo wl
filename:       /lib/modules/3.8.0-21-generic/kernel/drivers/net/wireless/wl.ko
srcversion:     49E2D90EE4D6877632DEDB0
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000435Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A99Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Dsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Asv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
depends:        lib80211
vermagic:       3.8.0-21-generic SMP mod_unload modversions 686 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           name:string

```

---

### Post by varunendra on 2013-05-21
> **bagelong said:**
> ```

long@long-Lenovo:~$ cat /etc/modprobe.d/blacklist.conf | tail -4
# really needed.
blacklist amd76x_edac
blacklist brcmsmac
blacklist brcmsmac

```

I think I got that corrected.  Don't remember running the corrected code twice.  Does it matter that it is repeated?
Not really, but let's get rid of it anyway -
```
sudo sed -i '/brcmsmac/ d' /etc/modprobe.d/blacklist.conf
echo "blacklist brcmsmac" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
The first command will delete both lines, the second one add one.

The bad line is gone, so am not sure what triggered that error message. The wl driver also seems in place. Maybe just do a restart and let us know if everything is fine or not.

---

### Post by bagelong on 2013-05-21
> **varunendra said:**
> 
The bad line is gone, so am not sure what triggered that error message. The wl driver also seems in place. Maybe just do a restart and let us know if everything is fine or not.

I had forgotten to run the corrected code after removing the incorrect one.

---

### Post by Hadaka on 2013-05-21
This is for the next kernel update.
please do..

```
gedit vsf_update
```

copy and paste this into the editor..

```
####......VSF ver1.0........RUN THIS FILE WITH THE NEXT KERNEL UPDATE ####

sudo su                          
modprobe -rfv wl
cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless
depmod -a
modprobe -v wl
update-initramfs -u
exit
 
```
save and close gedit

---

### Post by bagelong on 2013-05-21
Basically, I ran the corrected blacklist codes earlier to get rid of the incorrect line and add the correct one.  I then ran through the code in step 8 again.  Since that time, I have had no indication that wifi is available in the network manager.

---

### Post by bagelong on 2013-05-21
> **Hadaka said:**
> This is for the next kernel update.
please do..

```
gedit vsf_update
```

copy and paste this into the editor..

```
####......VSF ver1.0........RUN THIS FILE WITH THE NEXT KERNEL UPDATE ####

sudo su                          
modprobe -rfv wl
cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless
depmod -a
modprobe -v wl
update-initramfs -u
exit
 
```
save and close gedit

Done.  Reboot?

---

### Post by Hadaka on 2013-05-21
yes...but...that is just for the NEXT kernel update..has nothing to do
with what we are doing now,,
but yes...reboot and after please run again..

```

cat /etc/modprobe.d/blacklist.conf | tail -4
```

---

### Post by bagelong on 2013-05-21
```

long@long-Lenovo:~$ cat /etc/modprobe.d/blacklist.conf | tail -4
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist brcmsmac

```

This is now correct, isn't it?

---

### Post by Hadaka on 2013-05-21
YES it is,,,,good job,,
please do ..
```
sudo modprobe wl
```
you may have to unplug the cable for wireless to work...
post back.

---

### Post by varunendra on 2013-05-21
> **Hadaka said:**
> 
```
gedit vsf_update
```...

```
####......**[COLOR="#FF0000"]VSF ver1.0[/COLOR]**........RUN THIS FILE WITH THE NEXT KERNEL UPDATE ####
 
```

:lolflag:
I guess a memorial statue is all that is left :P

But the idea of a ready-to-use script is good, something like the "autorun.sh" in some realtek drivers. I think I'll edit the 'workaround' to include such a script to do everything in one-go (something I refrained from earlier, but seems okay now seeing how many things may go wrong in manual entry of commands).

---

### Post by bagelong on 2013-05-21
> **varunendra said:**
> :lolflag:
I guess a memorial statue is all that is left :P

But the idea of a ready-to-use script is good, something like the "autorun.sh" in some realtek drivers. I think I'll edit the 'workaround' to include such a script to do everything in one-go (something I refrained from earlier, but seems okay now [COLOR="#FF0000"]seeing how many things may go wrong in manual entry of commands[/COLOR]).

VSF lives on!!  

Ah yes, making fun of the noob and his terminal skills.

I ran "sudo modprobe wl" and I still show no sign of active wifi - wifi does not show at all in the network indicator.  Not sure what happened, but I now think I have discovered problem #3, because I have never been here before.

---

### Post by varunendra on 2013-05-21
Nope! My 'lol' was directed at Hadaka's sense of humour (which again wasn't a humour about you, it's just about our own personal chit-chat in the background :))
> **bagelong said:**
> I ran "sudo modprobe wl" and I still show no sign of active wifi - wifi does not show at all in the network indicator.
Let us check the basics again. Please post outputs of -
```
lspci -nnk | grep -iA2 net
rfkill list all
dmesg | grep -ie wl -e net
```

---

### Post by bagelong on 2013-05-21
Yes, I tried to edit my post above to reflect two points: 

1.) I am in agreement with your greatness being recognized with the VSF memorial statue, or perhaps a public building in honor of VSF would be more appropriate.

2.) The red text above (post #56) is an obvious and appropriate reference to my dominance of the copy and paste

DISCLAIMER - ALL OF THE ABOVE WAS TYPED IN A SARCASTIC/JESTING TONE  

I will get to work on this some time this evening.  My wife is not pleased with the inability to surf the internet unencumbered by cables and wires, so we must work quickly!

---

### Post by bagelong on 2013-05-21
> **varunendra said:**
> 
```
lspci -nnk | grep -iA2 net
rfkill list all
dmesg | grep -ie wl -e net
```

Will having a wired connection affect the output?

---

### Post by varunendra on 2013-05-21
> **bagelong said:**
> Will having a wired connection affect the output?

No, it won't. Especially if there is no hint of wifi at all !

---

### Post by bagelong on 2013-05-21
```

long@long-Lenovo:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0608]
	Kernel driver in use: bcma-pci-bridge
0c:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
	Subsystem: Lenovo Device [17aa:5000]
	Kernel driver in use: r8169
long@long-Lenovo:~$ rfkill list all
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no
long@long-Lenovo:~$ dmesg | grep -ie wl -e net
[    0.000000]   Transmeta GenuineTMx86
[    0.111951] NET: Registered protocol family 16
[    0.965413] NetLabel: Initializing
[    0.965414] NetLabel:  domain hash size = 128
[    0.965415] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.965424] NetLabel:  unlabeled traffic allowed by default
[    1.009714] NET: Registered protocol family 2
[    1.009894] NET: Registered protocol family 1
[    1.268421] audit: initializing netlink socket (disabled)
[    1.670986] NET: Registered protocol family 10
[    1.671123] NET: Registered protocol family 17
[    1.730642] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   16.125375] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.577237] type=1400 audit(1369140559.411:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=653 comm="apparmor_parser"
[   16.577244] type=1400 audit(1369140559.411:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=654 comm="apparmor_parser"
[   17.256607] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   17.485446] NET: Registered protocol family 31
[   17.515744] wl: module license 'unspecified' taints kernel.
[   17.745353] thinkpad_acpi: http://ibm-acpi.sf.net/
[   21.466831] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.609708] IPv6: ADDRCONF(NETDEV_UP): eth6: link is not ready
[   22.609961] IPv6: ADDRCONF(NETDEV_UP): eth6: link is not ready
[   23.525300] type=1400 audit(1369140566.367:11): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1014 comm="apparmor_parser"
[   57.717820] IPv6: ADDRCONF(NETDEV_CHANGE): eth6: link becomes ready

```

---

### Post by Hadaka on 2013-05-21
Hi, looks like were are back to where we started..


Kernel driver in use: bcma-pci-bridge

please post ..
```
cat /etc/modules
lsmod
```
thanks.

---

### Post by bagelong on 2013-05-21
```

long@long-Lenovo:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
wl
wl
long@long-Lenovo:~$ lsmod
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  0 
bnep                   17669  2 
snd_hda_codec_hdmi     36185  1 
snd_hda_codec_conexant    52256  1 
joydev                 17097  0 
coretemp               13131  0 
kvm                   376505  0 
uvcvideo               71279  0 
aesni_intel            18156  0 
aes_i586               16995  1 aesni_intel
videobuf2_vmalloc      12920  1 uvcvideo
xts                    12749  1 aesni_intel
videobuf2_memops       13042  1 videobuf2_vmalloc
lrw                    13057  1 aesni_intel
btusb                  17986  0 
gf128mul               14503  2 lrw,xts
videobuf2_core         39161  1 uvcvideo
thinkpad_acpi          69384  0 
videodev               95806  2 uvcvideo,videobuf2_core
ablk_helper            13357  1 aesni_intel
nvram                  13986  1 thinkpad_acpi
lp                     13299  0 
snd_hda_intel          38307  3 
snd_hda_codec         117580  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
i915                  535507  3 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
wl                   2438754  0 
bluetooth             202069  11 bnep,btusb,rfcomm
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
cryptd                 15613  1 ablk_helper
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
drm_kms_helper         47545  1 i915
snd                    56485  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
psmouse                81038  0 
drm                   228750  4 i915,drm_kms_helper
video                  18894  1 i915
parport                40753  3 lp,ppdev,parport_pc
microcode              18286  0 
serio_raw              13031  0 
lib80211               14040  1 wl
soundcore              12600  1 snd
wmi                    18590  0 
rtsx_pci_ms            12875  0 
memstick               15842  1 rtsx_pci_ms
mei                    36197  0 
lpc_ich                16925  0 
bcma                   39645  0 
mac_hid                13037  0 
i2c_algo_bit           13197  1 i915
rtsx_pci_sdmmc         17238  0 
r8169                  61531  0 
ahci                   25507  2 
rtsx_pci               32018  2 rtsx_pci_ms,rtsx_pci_sdmmc
libahci                26108  1 ahci

```

---

### Post by Hadaka on 2013-05-21
please do..
```
sudo modprobe -rfv bcma
sudo modprobe wl
lsmod
```
;)

---

### Post by bagelong on 2013-05-21
```

long@long-Lenovo:~$ sudo modprobe -rfv bcma
[sudo] password for long: 
rmmod bcma
long@long-Lenovo:~$ sudo modprobe wl
long@long-Lenovo:~$ lsmod
Module                  Size  Used by
parport_pc             27504  0 
ppdev                  12817  0 
rfcomm                 37420  0 
bnep                   17669  2 
snd_hda_codec_hdmi     36185  1 
snd_hda_codec_conexant    52256  1 
joydev                 17097  0 
coretemp               13131  0 
kvm                   376505  0 
uvcvideo               71279  0 
aesni_intel            18156  0 
aes_i586               16995  1 aesni_intel
videobuf2_vmalloc      12920  1 uvcvideo
xts                    12749  1 aesni_intel
videobuf2_memops       13042  1 videobuf2_vmalloc
lrw                    13057  1 aesni_intel
btusb                  17986  0 
gf128mul               14503  2 lrw,xts
videobuf2_core         39161  1 uvcvideo
thinkpad_acpi          69384  0 
videodev               95806  2 uvcvideo,videobuf2_core
ablk_helper            13357  1 aesni_intel
nvram                  13986  1 thinkpad_acpi
lp                     13299  0 
snd_hda_intel          38307  3 
snd_hda_codec         117580  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
i915                  535507  3 
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
wl                   2438754  0 
bluetooth             202069  11 bnep,btusb,rfcomm
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
cryptd                 15613  1 ablk_helper
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
drm_kms_helper         47545  1 i915
snd                    56485  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,thinkpad_acpi,snd_seq_device
psmouse                81038  0 
drm                   228750  4 i915,drm_kms_helper
video                  18894  1 i915
parport                40753  3 lp,ppdev,parport_pc
microcode              18286  0 
serio_raw              13031  0 
lib80211               14040  1 wl
soundcore              12600  1 snd
wmi                    18590  0 
rtsx_pci_ms            12875  0 
memstick               15842  1 rtsx_pci_ms
mei                    36197  0 
lpc_ich                16925  0 
mac_hid                13037  0 
i2c_algo_bit           13197  1 i915
rtsx_pci_sdmmc         17238  0 
r8169                  61531  0 
ahci                   25507  2 
rtsx_pci               32018  2 rtsx_pci_ms,rtsx_pci_sdmmc
libahci                26108  1 ahci

```

Reboot?

---

### Post by Hadaka on 2013-05-21
yes

---

### Post by bagelong on 2013-05-21
Still no wifi.

---

### Post by Hadaka on 2013-05-21
ok, power cycle the modem...off (20 sec) ON
then...do..
**SEE NEXT POST**
```

sudo su                           modprobe -rfv wl cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless depmod -a modprobe -v wl update-initramfs -u exit 
```


**SEE NEXT POST**

---

### Post by Hadaka on 2013-05-21
re posting..
```
sudo su                          
modprobe -rfv wl
cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless
depmod -a
modprobe -v wl
update-initramfs -u
exit
 
```

---

### Post by bagelong on 2013-05-21
Just the modem, or the router also?
Run that as one line of code?  Looks like several commands that were previously run separately.

---

### Post by Hadaka on 2013-05-21
yes both...router and modem
the copy and paste went wrong..so see the post after
that one.

---

### Post by bagelong on 2013-05-21
```

root@long-Lenovo:/home/long# cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless
cp: cannot stat &#8216;wl.ko&#8217;: No such file or directory

```

Did I need to navigate to that directory?

---

### Post by Hadaka on 2013-05-21
you should have that directory with the wl.ko file from
when you compiled and built the driver.
perhaps this is why it is not working now.
start at step one of the VSF file and do it again.

---

### Post by bagelong on 2013-05-21
That directory is still on my desktop, with the wl.ko file present.  However, previously I navigated to that directory before running those commands.

```

cd ~/Desktop/hybrid-portsrc_x86_32-v5_100_82_112

```

---

### Post by Hadaka on 2013-05-21
ok, do it that way then,,and i will modify your update file
as should you...but later...run the commands at the desktop location
so YES navigate to the file..run the commands

---

### Post by bagelong on 2013-05-21
> **Hadaka said:**
> ok, do it that way then,,and i will modify your update file
as should you...but later...run the commands at the desktop location
so YES navigate to the file..run the commands

Something is not going right.  I am not sure what I am doing wrong, but based upon the original VSF, I was remaining in the extracted folder after step 7 when I initially ran through these steps.  As recommended, I have navigated back to that extracted folder (which includes the wl.ko file) and I went through the codes in post #69, but still I am getting no indication that wi-fi is active.  I am sorry, but I think I am the weak link here, and I really don't understand where I am failing.

---

### Post by Hadaka on 2013-05-21
lets take a look at something..
this is one command...long one...copy and paste it...
```
ls /lib/modules/`uname -r`/kernel/drivers/net/wireless | grep -i wl.ko
```
see if it comes up blank.
thanks.

---

### Post by bagelong on 2013-05-21
```

long@long-Lenovo:~$ ls /lib/modules/`uname -r`/kernel/drivers/net/wireless | grep -i wl.ko
wl.ko

```

---

### Post by Hadaka on 2013-05-21
ok try this...i see you are not out of root prompt...
to verify...type exit and bring up a new terminal
then..do
```
cd Desktop
sudo su                          
modprobe -rfv wl
cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless
depmod -a
modprobe -v wl
update-initramfs -u
exit

```
see how that goes

---

### Post by bagelong on 2013-05-22
```

root@long-Lenovo:/home/long/Desktop# cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless
cp: cannot stat &#8216;wl.ko&#8217;: No such file or directory

```

---

### Post by Hadaka on 2013-05-22
ok..do this
type exit...bring up a new terminal.again
then do.
```
cd ~/Desktop/hybrid-portsrc_x86_64-v5_100_82_112
 sudo su                          
modprobe -rfv wl
cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless
depmod -a
modprobe -v wl
update-initramfs -u
exit

```
that should work

---

### Post by bagelong on 2013-05-22
Instructions in post #81 above did not work, so here is what i did:

I reinstalled the broadcom driver from the Ubuntu Software Center
I ran all steps of VSF again
Wi-fi up and running with a good connection.

---

### Post by Hadaka on 2013-05-22
thats weird....ok
as long as it works.
varunendra will no doubt want to see this as well,

---

### Post by bagelong on 2013-05-22
Went ahead and did a reboot, and wi-fi is gone again.  I am beginning to think a better solution is to do a fresh install of 12.04.  Not sure I am man enough to help you guys resolve this.  

I do, however, appreciate so much what you two have done for me.  I think I am just failing somewhere along the way, and it doesn't seem to be moving much closer to a final resolution.

---

### Post by Hadaka on 2013-05-22
You have done an awesome job with this, I am not sure why
its not sticking, perhaps if you work with varunendra and do
one command at a time, the reason it fails on boot will be found.
but, you have been great..and thank you for hanging in there with this.

---

### Post by Hadaka on 2013-05-22
one thing i did notice, and it shouldnt make a difference.
your /etc/modules looks like this..
```
lp
wl
wl
```
you can..
```
sudo gedit /etc/modules
```
back space -remove- one wl
save and close gedit

---

### Post by varunendra on 2013-05-22
Ah, I see I missed a long day! Times goes by really fast some times..
> **bagelong said:**
> I am beginning to think a better solution is to do a fresh install of 12.04.
bagelong,

First of all, you don't need to cover up something that is apparently our failure. We try what we know from our experience and experience comes from trying and occasionally failing. For example, the post #63 is showing something that I obviously overlooked earlier (due to lack of much experience with bcma driver), and the fix is as easy as blacklisting it too.

Secondly, like I said earlier, you don't need to build the driver everytime once it is built for the current kernel. Just keep it somewhere and copy it over if required at all (and even that shouldn't be required unless we are making some mistake).

Above all, if you are able to build the driver each time (the wl.ko file) and also able to load it and get it working, you have already gone past the most critical and probably the difficult part. The automatic loading, conflict with another driver, etc. issues can be caused by just a few things and there can be multiple workarounds for them. We are just trying to make it happen naturally, otherwise there are ways to 'force' it, so you don't have to do it manually each time.


That being said, if we are not dragging you too far, please try -
```
echo "blacklist bcma" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
This is the same thing that we did with "brcmsmac" driver earlier, this is one more to be blocked. As per the output in your post #63, the wl driver is already loading fine. It's just that the bcma driver takes over earlier (and then doesn't work, stupid little driver!)

**@ Hadaka,**
I noticed a minor mistake you did in post #64. You 'modprobe'd the wl driver while it was already loaded. I think you overlooked it as soon as you saw "bcma-pci-bridge" in lspci output (I have done that too in the past ;)). It had to be unloaded, then loaded again.

**@ bagelong,**
Even if everything fails but the wl driver we built is working (when manually loaded), I can guarantee that I can make it load automatically. You won't have to do anything manually until next kernel upgrade. (wow! I hope that's not too big a promise :P)

However, when you say "good connection", just run -
```
lspci -nnk | grep -iA2 net
```
and check which driver is loaded for your broadcom wireless card *(Kernel driver in use)*. That would be the one we want. If that happens to be the "wl" driver we are working so hard for, then we are on the right track, probably at the 'solution' end of it.

---

### Post by bagelong on 2013-05-22
So, I reinstalled the broadcom driver, then reapplied VSF and all is working.  I blacklisted the bcma driver as above.  Here is the output of the code from above, indicating the correct driver is in use.  

```

long@long-Lenovo:~$ lspci -nnk | grep -iA2 net
03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Broadcom Corporation Device [14e4:0608]
	Kernel driver in use: wl
0c:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 07)
	Subsystem: Lenovo Device [17aa:5000]
	Kernel driver in use: r8169

```

---

### Post by bagelong on 2013-05-22
```

long@long-Lenovo:~$ cat /etc/modprobe.d/blacklist.conf
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

# ugly and loud noise, getting on everyone's nerves; this should be done by a
# nice pulseaudio bing (Ubuntu: #77010)
blacklist pcspkr

# EDAC driver for amd76x clashes with the agp driver preventing the aperture
# from being initialised (Ubuntu: #297750). Blacklist so that the driver
# continues to build and is installable for the few cases where its
# really needed.
blacklist amd76x_edac
blacklist brcmsmac
blacklist bcma

```

---

### Post by varunendra on 2013-05-22
Both look good to me, does it hold after reboot? And is the performance the 'good' one?

Because at least one user has reported that for him the brcmsmac was performing better. But it can be different for different people.

---

### Post by bagelong on 2013-05-23
> **varunendra said:**
> Both look good to me, does it hold after reboot? And is the performance the 'good' one?

Because at least one user has reported that for him the brcmsmac was performing better. But it can be different for different people.

It is holding after reboot.  Guess we'll have to see what happens with the next kernel update.   

Any output that would be helpful to you?

---

### Post by bagelong on 2013-05-23
Another quick question - is 72 mbps the max connection speed for this wireless adapter?

---

### Post by varunendra on 2013-05-23
> **bagelong said:**
> It is holding after reboot.  Guess we'll have to see what happens with the next kernel update.
That's a good news.

With a new kernel update, either you'll get a fixed driver (by accepting suggestion from the "Additional Drivers" program to install the proprietary driver), or will have to compile it again (cd <to the directory> --> make --> complete step 8 once). Blacklisting the native drivers or adding "wl" to "/etc/modules" file won't be needed again. (in fact, you'll have to Undo these two things if you wish to try the native drivers again).

> **bagelong said:**
> Another quick question - is 72 mbps the max connection speed for this wireless adapter?
The adapter itself is 'b/g/n' type, so it *should* support N-channel speed that is upto 150 or 300 Mbps. However, I am not sure about whether the wl driver will support that much speed or not. It can be limited due to the incapability of the driver, or the router or its settings.

To see the speeds supported by your router, please post -
```
sudo iwlist scan
```

With my very limited knowledge about wireless channels and router support for related speeds, I think anything above 54Mbps means there IS support for N-channel. If so, we should expect upto 150 or even 300 Mbps speed.

---

### Post by bagelong on 2013-05-23
```

long@long-Lenovo:~$ sudo iwlist scan
[sudo] password for long: 
eth7      Scan completed :
          Cell 01 - Address: 58:6D:8F:90:E0:23
                    ESSID:"Cisco47799"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-31 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7F0050F204104A00011010440001021041000100103B00010310470010B4BDE38EDD78AAD1B25D93F1902999EE10210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30321042000234321054000800060050F20400011011000D4C696E6B737973204532353030100800020084103C000103
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: 58:6D:8F:90:E0:25
                    ESSID:"Cisco47799-guest"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:5/5  Signal level:-31 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 03 - Address: 58:6D:8F:F9:51:BE
                    ESSID:"Bear Park"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:3/5  Signal level:-69 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD750050F204104A0001101044000102103B0001031047001078B7371383764895946E0366A91BDF3810210005436973636F10230003574150102400033132331042000531323334351054000800060050F204000110110009426561722D5061726B10080002200C103C0001011049000600372A000120
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 04 - Address: 5E:6D:8F:F9:51:BE
                    ESSID:"Bear Park-guest"
                    Mode:Managed
                    Frequency:2.427 GHz (Channel 4)
                    Quality:3/5  Signal level:-69 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
          Cell 05 - Address: 84:1B:5E:C9:EC:19
                    ESSID:"NETGEAR46"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:2/5  Signal level:-79 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD840050F204104A00011010440001021041000100103B00010310470010CAD05FD514413B9E438032513175D6491021000D4E4554474541522C20496E632E1023000A574E44523337303076331024000A574E44523337303076331042000230311054000800060050F20400011011000A574E4452333730307633100800020084103C000103
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 06 - Address: 2C:B0:5D:45:24:AD
                    ESSID:"hester_EXT"
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-81 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD7E0050F204104A00011010440001021041000100103B000103104700101D8ACAE84646E450A2AB4CB58A2C2B431021000D4E4554474541522C20496E632E10230008574E33303030525010240008574E3330303052501042000230311054000800060050F204000110110008574E333030305250100800020084103C000101
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s

lo        Interface doesn't support scanning.

eth6      Interface doesn't support scanning.

```

---

### Post by Hadaka on 2013-05-23
hi, is this your router? 

ESSID:"Cisco47799"

if yes, then log into it
and change it to wpa2-aes  
wpa2-psk  anything but TKIP
thanks.

---

### Post by bagelong on 2013-05-23
I am not sure where that TKIP setting comes from because I have security set up as WPA2/WPA mixed mode

---

### Post by Hadaka on 2013-05-23
Its from the router.
rummage around in the router, you'll find it.
or..gasp ! read the manual.;)

---

### Post by bagelong on 2013-05-23
Just rummaged through every setting and I don't see that as an option anywhere.

---

### Post by varunendra on 2013-05-24
> **bagelong said:**
> I have security set up as **[COLOR="#FF0000"]WPA2/WPA mixed mode[/COLOR]**
Wah...?? :shock:
That 'mixed mode' thing is 'Strongly' discouraged with Linux. Set it to WPA2-PSK only.

To be honest, I only know about wireless routers as much as I have read on these forums. I don't personally have a wireless router or a wireless network available to do experiments myself (one of the things I miss the most.. :( ). In fact I don't even understand most part of the 'iwlist scan' command output. So.. Hadaka is a much better help on that one (seems to have first hand experience with these).

As for navigating the encryption settings, search the net for "xxxxxx user manual", where "xxxxxx.." is the exact model of your router. Or give us its link (or model no.), may be we could look it up for you if it is hidden below some huge pile of text.

---

### Post by bagelong on 2013-06-02
Seems stable each time until there is an update that requires a reboot, then I have to reapply VSF.  Quick question, since I am using this driver, how would I know that an update fixed my wireless issue, since the Broadcom driver is blacklisted?

---

### Post by varunendra on 2013-06-03
The driver itself is nothing to worry about since any kernel upgrade will automatically break it.

But the blacklist, yes you'll have to manually 'undo' the custom blacklistings to be able to try the native brcmsmac or the default proprietary wl driver. If they don't work, or work poorly, they are not yet fixed and you can safely repeat... what do you guys call it... uh..

Unfortunately, I don't know of a better way to test this.

---

### Post by kajkob on 2013-06-08
First of all, thanks so much for your help. I'm a noob to linux, but really like Linux Mint and installed Mint 14 on my HP Folio 13 - 1020US. I have since reinstalled Mint 15 & Ubuntu 13.04 and the wireless has been the bain of my existence for 3 days. 6+ hours of searching etc. and this has been the most helpful thread so far.

Having said that, I successfully followed your #31 "VSF" post and for the first time, I connected to my WiFi. However, it is painfully slow (read: unusable) and sometimes just disconnects. You mentioned some people had better performance with another driver (brcm ?) Is there any advice or somewhere you can point me to on how to install that driver AFTER having done your steps. Appreciate it.

Here's some basics to start with:
```

description: Wireless interface
       product: BCM4313 802.11b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth1
       version: 01
       serial: c0:18:85:07:b7:fd
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.100.82.112 latency=0 multicast=yes wireless=IEEE 802.11
       resources: irq:18 memory:c2600000-c2603fff

```

lspci -nn | grep 0280
```
Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
```

lsmod
```

Module                  Size  Used by
lib80211_crypt_tkip    17379  0 
wl                   2573614  0 
lib80211               14352  2 wl,lib80211_crypt_tkip
nls_iso8859_1          12713  1 
michael_mic            12612  0 
arc4                   12615  0 
parport_pc             28152  0 
ppdev                  17073  0 
rfcomm                 42641  0 
bnep                   18036  2 
bluetooth             228619  10 bnep,rfcomm
binfmt_misc            17500  1 
coretemp               13355  0 
kvm                   443165  0 
ghash_clmulni_intel    13259  0 
aesni_intel            55399  0 
aes_x86_64             17255  1 aesni_intel
xts                    12885  1 aesni_intel
lrw                    13257  1 aesni_intel
gf128mul               14951  2 lrw,xts
ablk_helper            13597  1 aesni_intel
cryptd                 20373  3 ghash_clmulni_intel,aesni_intel,ablk_helper
joydev                 17377  0 
hid_generic            12540  0 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_idt      70256  1 
dm_multipath           22843  0 
snd_hda_intel          39619  3 
scsi_dh                14843  1 dm_multipath
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
microcode              22881  0 
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
uvcvideo               80847  0 
snd_seq_midi           13324  0 
videobuf2_vmalloc      13056  1 uvcvideo
snd_seq_midi_event     14899  1 snd_seq_midi
usbhid                 47074  0 
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
snd_rawmidi            30180  1 snd_seq_midi
hid                   101002  2 hid_generic,usbhid
videodev              129260  2 uvcvideo,videobuf2_core
psmouse                95870  0 
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
rtsx_pci_ms            13011  0 
serio_raw              13215  0 
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
memstick               16554  1 rtsx_pci_ms
snd_timer              29425  2 snd_pcm,snd_seq
lpc_ich                17061  0 
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_idt,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12680  1 snd
mei                    41158  0 
lp                     17759  0 
mac_hid                13205  0 
parport                46345  3 lp,ppdev,parport_pc
btrfs                 785967  0 
zlib_deflate           26885  1 btrfs
libcrc32c              12615  1 btrfs
dm_raid45              76725  0 
xor                    17116  1 dm_raid45
dm_mirror              21946  0 
dm_region_hash         20820  1 dm_mirror
dm_log                 18529  3 dm_region_hash,dm_mirror,dm_raid45
usb_storage            57204  1 
rtsx_pci_sdmmc         17475  0 
i915                  600351  3 
rtsx_pci               33355  2 rtsx_pci_ms,rtsx_pci_sdmmc
i2c_algo_bit           13413  1 i915
drm_kms_helper         49394  1 i915
r8169                  67446  0 
drm                   286313  4 i915,drm_kms_helper
ahci                   25731  2 
libahci                31364  1 ahci
wmi                    19070  1 hp_wmi
video                  19390  1 i915

```

---

### Post by varunendra on 2013-06-08
Welcome to the forums kajkob :)

While I search the brcmsmac fix and take a close look myself, let's do a sanity check in the meanwhile. Please follow the "Wireless Script" link in my signature, follow the instructions there, and post back the result of the script here (the wireless-info.txt file or its contents or its pastebin link).

And please confirm - have you tried any other fixes as well in the parallel or in the past? (on the same installation). If yes, please provide the link to the solution you followed (if you remember, otherwise not necessary).

I hope we can make it at least 'usable'.


**EDIT:**
For reference : [http://ubuntuforums.org/showthread.php?t=2140640&p=12652119#post12652119](http://ubuntuforums.org/showthread.php?t=2140640&p=12652119#post12652119)
[http://ubuntuforums.org/showthread.php?t=2148444&p=12663032#post12663032](http://ubuntuforums.org/showthread.php?t=2148444&p=12663032#post12663032) (apparently not applicable to 4727)

---

### Post by kajkob on 2013-06-10
Thanks for the quick response, unfortunately I was gone for the weekend. While trying to retrace my steps, I realized I may have made a huge tiny mistake.. at some point I followed the directions in post #2 at 

[http://ubuntuforums.org/showthread.php?t=2148444](http://ubuntuforums.org/showthread.php?t=2148444)

using the firmware linked in #4 on that page ([Broadcom_Firmware_070513.tar.gz herunterladen]("http://media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz")) basically flashing the firmware of the card. Now, the wireless won't connect at all again as even just hitting the wireless button to turn it on does nothing..and I can't even turn it on in Windows any longer! Am I correct that flashing the firmware of the wireless card hardware would affect it in any OS and most importantly, how would I reverse this? At this point I think I may have caused more of a problem than just the drivers... please help!

FYI - I flashed the machine's BIOS to an updated version (and back for good measure) which did not help. Can't turn on the wireless card in any OS..

---

### Post by varunendra on 2013-06-10
Hi,

Before answering your questions, I'd ask you to please not panic! It can be something simple, not necessarily something as severe as you think.

> **kajkob said:**
> at some point I followed the directions in post #2 at 

[http://ubuntuforums.org/showthread.php?t=2148444](http://ubuntuforums.org/showthread.php?t=2148444)

using the firmware linked in #4 on that page ([Broadcom_Firmware_070513.tar.gz herunterladen]("http://media.cdn.ubuntu-de.org/forum/attachments/56/18/5007272-Broadcom_Firmware_070513.tar.gz")) basically flashing the firmware of the card. Now, the wireless won't connect at all again as even just hitting the wireless button to turn it on does nothing..and I can't even turn it on in Windows any longer!
I can't say why you are unable to turn it on even in windows, but I can say with 100% confidence that the firmware you downloaded has nothing to do with it.

Like I mentioned within the brackets in the Edit part of my previous post, I don't think it is even applicable to your card, although I have seen praseodym suggesting the same firmware package in a few threads (and he is a lot more experienced than me). Besides, the firmware files like this are dynamically loaded by the driver in the computer's memory, not the card itself (I may be wrong on this, but I'm sure it is loaded in a 'volatile' area). It is not the static firmware of the card. So even if you somehow manage to load an incorrect firmware for a card, it can't affect it permanently.

> Am I correct that flashing the firmware of the wireless card hardware would affect it in any OS and most importantly, how would I reverse this? At this point I think I may have caused more of a problem than just the drivers... please help!
Firstly, I don't think you can even flash a wireless card actually. Like I mentioned above, the firmware loaded by the driver is the dynamic part that is required for certain functions. It gets reset on a reboot (or is supposed to). In some cases however, the static firmware CAN get stuck resulting in weird behaviour. In that case, the usual recommendation is to just disconnect it from all power sources for a few minutes (20 seconds to 10 minutes, depending upon various factors). It is easier to do in a desktop, but in a laptop, it may be a bit difficult.

Now before trying anything else, I'd once again ask you to just run the "Wireless script" I mentioned in my previous post, and post back its results here. We may get significant hints in it about the problem.


**PS:**
Although I wouldn't recommend it yet, if you are absolutely sure that the firmware of the card is stuck, you may try this -

If you reverted the version of the BIOS, upgrade it again. Then reset it to default settings (although it should automatically be done during upgrade, but just in case). The option to reset to default is usually listed as "Load Defaults" or "Load Optimized Defaults" etc. in the "Exit" menu of the BIOS. Try whatever you have in yours.

If this doesn't make it work in either OS, then try disconnecting the wireless card. Most often, the wireless card is placed in a user-accessible area at the bottom of the laptop chasis. See if you can access it after removing the cover panels at the bottom. If you can, just disconnect the two plug-type wires connected to it, remove the screw(s) and pull it out. Leave it for about 10 minutes then re-seat in its place like before. As far as I know, this is all you can do with it (apart from entirely replacing it with another one).

---

### Post by kajkob on 2013-06-10
> It is not the static firmware of the card. So even if you somehow  manage to load an incorrect firmware for a card, it can't affect it  permanently.

That's great news, thanks for the explanation. 

> If you reverted the version of the BIOS, upgrade it again. Then reset it to default settings..

Did this last night actually and it indeed 'reset' everything allowing me to turn the WiFi card on with the hardware switch again, both in Windows and Linux

> And please confirm - have you tried any other fixes as well in the parallel or in the past?

I can't remember everything, but I reinstalled Linux after some of the attempts so they were wiped. Did not try the b43 drivers as they state no support for 14e4:4727. I did of course try the suggested Broadcom drivers first which failed. Did the firmware flash as mentioned on this current install and then tried your solution.

> Now before trying anything else, I'd once again ask you to just run the  "Wireless script" I mentioned in my previous post, and post back its  results here. We may get significant hints in it about the problem.

Sorry I didn't reailze I could run that without the wireless card being on at all, so I panicked a bit as you said. Also, to clarify, the card does turn on now again in Linux as mentioned but was only able to load one page very slowly and then disconnected. Here are the results:

```

*************** info trace ***************

***** uname -a *****

Linux karl-FolioMint 3.8.0-23-generic #34-Ubuntu SMP Wed May 29 20:22:58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    LinuxMint
Description:    Linux Mint 15 Olivia
Release:    15
Codename:    olivia

***** lspci *****

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:17f8]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: wl

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:2c07 Sunplus Innovation Technology Inc. 
Bus 001 Device 004: ID 0a5c:21e3 Broadcom Corp. 
Bus 002 Device 003: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver

***** iwconfig *****

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:239  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


***** rfkill *****

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: hp-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no

***** lsmod *****

wl                   2573614  0 
lib80211               14352  2 wl,lib80211_crypt_tkip

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth1  [Asus] ---------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Asus:           Infra, <MAC address removed>, Freq 2447 MHz, Rate 0 Mb/s, Strength 100 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.104
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             65.32.5.111
    DNS:             65.32.5.112


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"Asus"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:5/5  Signal level:-6 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s


***** resolv.conf *****

nameserver 127.0.1.1
search cfl.rr.com

nameserver 208.67.222.222
nameserver 208.67.220.220

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcma
blacklist brcmsmac
blacklist 43
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** dmesg *****

[    4.327544] wl: module license 'unspecified' taints kernel.
[    4.509158] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.112

****************** done ******************


```

---

### Post by varunendra on 2013-06-10
> **kajkob said:**
> ....Also, to clarify, the card does turn on now again in Linux as mentioned but was only able to load one page very slowly and then disconnected.
Aha!! At least we got back to where we began :D

Possible culprit no.1 -
> **kajkob said:**
> 
```

***** iwlist *****

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"Asus"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:5/5  Signal level:-6 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/**[COLOR="#FF0000"]WPA2 Version 1[/COLOR]**
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Authentication Suites (1) : PSK
                    IE: **[COLOR="#FF0000"]WPA Version 1[/COLOR]**
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP **[COLOR="#FF0000"]TKIP[/COLOR]**
                        Authentication Suites (1) : PSK
                    Encryption key:on

```
Please change the encryption settings in your router to pure WPA2-PSK (AES) only. No WPA/WPA2 mixed mode, no TKIP. This is something I'd ask you to do regardless of the driver in use.

Then, for your wireless connection in Network Manager, make sure "Method" under IPv6 is set to "Ignore" and the same under IPv4 is set to "Automatic (DHCP) address only". This will allow you to define your own DNS for the connection. Then in the "DNS servers" field, enter the addresses of Google's open DNS servers - type exactly (without the double-quotes) : "8.8.8.8, 8.8.4.4"
Click "Save" > close.

Then restart both your router and laptop, and try to connect. If it is still slow, post back the results of -
```
ifconfig
iwconfig
sudo iwlist eth1 scan
nm-tool
```

---

### Post by kajkob on 2013-06-14
Wow, I went way down this rabbit hole... Went on a bit of tangent when messing with the WiFi and decided to upgrade to a new router this week (Asus RT-N66U) which is set up and working fine. Now, after extensive messing with many things at once (SSD TRIM support, etc) which I now think was a mistake, I had to start completely over and reinstalled. Now new issues arrise.. this time when I try to compile the the driver, I get the following error message:

```
karl@karlFolioMint ~/Desktop/hybrid-portsrc_x86_64-v5_100_82_112 $ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.9.6-030906-generic'
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  LD      /home/karl/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/built-in.o
  CC [M]  /home/karl/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/src/shared/linux_osl.o
  CC [M]  /home/karl/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_linux.o
  CC [M]  /home/karl/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_iw.o
  CC [M]  /home/karl/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/src/wl/sys/wl_cfg80211.o
  LD [M]  /home/karl/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/wl.o
  Building modules, stage 2.
Wireless Extension is the only possible API for this kernel version
Using Wireless Extension API
  MODPOST 1 modules
WARNING: modpost: missing MODULE_LICENSE() in /home/karl/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/wl.o
see include/linux/module.h for more information
WARNING: modpost: Found 1 section mismatch(es).
To see full details build your kernel with:
'make CONFIG_DEBUG_SECTION_MISMATCH=y'
  CC      /home/karl/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/wl.mod.o
  LD [M]  /home/karl/Desktop/hybrid-portsrc_x86_64-v5_100_82_112/wl.ko
make[1]: Leaving directory `/usr/src/linux-headers-3.9.6-030906-generic'

```

> If successful, you should see "wl.ko" file in the extracted directory.  If it is there, ONLY THEN proceed as follows (in the same terminal, same  directory) -

The wl.ko file is in the directory, but when I go onto the next steps this is what I get:
```
$ modprobe -rfv wl
FATAL: Module wl not found.

```

I think I should note that since I started over, the system setup may be different etc. so here is some other basic info that may come into play.

#cat /etc/lsb-release; uname -a
```
DISTRIB_ID=LinuxMint
DISTRIB_RELEASE=15
DISTRIB_CODENAME=olivia
DISTRIB_DESCRIPTION="Linux Mint 15 Olivia"
Linux karlFolioMint 3.9.6-030906-generic #201306131535 SMP Thu Jun 13 19:35:54 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

```

# lspci -nnk | grep -iA2 net
```

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:17f8]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader [10ec:5209] (rev 01)

```

# iwconfig
```

eth0      no wireless extensions.

lo        no wireless extensions.
```

Current blacklisted in /etc/modprobe.d/blacklist.conf:[INDENT]blacklist brmcsmac
blacklist bcma
blacklist ssb
blacklist b43
blacklist b43legacy
blacklist ndiswrapper
[/INDENT]

So I can't quite make it as far this time, any suggestions on  the make failure? Thanks

---

### Post by varunendra on 2013-06-15
The warning messeges you got are normal and there is nothing serious about them. We don't need to worry about warnings unless they translate into Errors. Only in that case do we need to take a close look at the warning messages to find out the reason for the error.

Like I mentioned in the [original post]("http://ubuntuforums.org/showthread.php?t=2140640&p=12629619#post12629619") that you were following, IF -
> **kajkob said:**
> The wl.ko file is in the directory
..then we are good to go ahead.

> ```
$ **modprobe [COLOR="#FF0000"]-r[/COLOR]fv wl**
FATAL: Module wl not found.

```
That command is meant to unload the wrong version of the wl driver if it is loaded. In your case it wasn't, hence the error. So no worries there (I should have made it clear in that post, sorry).
*For your info, the "-r" option in modprobe commands stands for "remove". Without it, the command does the opposite - that is, loads a driver. (-f is for "force", -v for "verbose").* :)

Also, why have you blacklisted ndiswrapper? Did you install it? It is absolutely not needed, although blacklisting won't have any effect (no need to blacklist something that doesn't even exist in the system), its presence make me suspicious that you might have tried too many random things -
> Current blacklisted in /etc/modprobe.d/blacklist.conf:[INDENT]blacklist brmcsmac
blacklist bcma
blacklist ssb
blacklist b43
blacklist b43legacy
**[COLOR="#FF0000"]blacklist ndiswrapper[/COLOR]**
[/INDENT]
In the same manner, you also don't need to blacklist b43, b43legacy or ssb. They won't get loaded for your particular card unless you force them to.

> any suggestions on  the make failure?
Like I mentioned above, warnings are normal and it wasn't a failure. The presence of wl.ko was a proof of success. Afterwards, the modprobe command tried to remove a driver which wasn't loaded, hence the error. So everything so far seems normal to me, and so you can proceed with the rest of the steps.

But if you have tried ndiswrapper, it may cause troubles if we still have its remnants. For now, just complete the steps for the compiled wl.ko driver and post back if we have any problems after that.

Thanks.

---

### Post by kajkob on 2013-06-15
> **varunendra said:**
> That command is meant to unload the wrong version of the wl driver if it is loaded. In your case it wasn't, hence the error. So no worries there (I should have made it clear in that post, sorry).
*For your info, the "-r" option in modprobe commands stands for "remove". Without it, the command does the opposite - that is, loads a driver. (-f is for "force", -v for "verbose").* :)

Like I said, total noob! Thanks for explaining. Sounds like I should have just kept going with the instructions... I will do that when I return tomorrow.

> **varunendra said:**
> Also, why have you blacklisted ndiswrapper? Did you install it?.. It is absolutely not needed, although blacklisting won't have any effect (no need to blacklist something that doesn't even exist in the system), its presence make me suspicious that you might have tried too many random things -

No, I did not explicitly install ndiswrapper or any of the other blacklisted drivers..but after all those forum posts, from my (mis?)understanding some drivers are part of the kernel itself, so I just blacklisted everything I knew I didn't want to use. I see that it's not necessary now. I'll report back..

---

### Post by kajkob on 2013-06-17
Well, all appears well! At least so far, the connection is stable and speeds acceptable. I do have a couple of related questions out of interest and for possible practical purposes later on..

You mentioned that building the driver from the source download will be necessary every time the kernel upgrades. The following post mentions locking the version of the driver, would this method be applicable with this solution? [ [http://askubuntu.com/questions/286734/how-to-downgrade-broadcom-wireless-drivers-bcmwl-kernel-source](http://askubuntu.com/questions/286734/how-to-downgrade-broadcom-wireless-drivers-bcmwl-kernel-source) ]

Also, how do I know/tell when the kernel will be upgraded. Is there an obvious designation in the updates that highlights a kernel upgrade?

Also, if for whatever reason I wanted to undo this process in the future, how would I go about doing so? I noticed previously that using ```
apt-get remove --purge bcmwl-kernel-source
``` did not work after the first time I followed these steps and I tried to reverse them.

Thanks again, learning lots!

---

### Post by kajkob on 2013-06-18
> **varunendra said:**
> 
Then restart both your router and laptop, and try to connect. If it is still slow, post back the results of -
ifconfig
iwconfig
sudo iwlist eth1 scan
nm-tool

Afraid I spoke too soon.. after a day of usage, the WiFi is back to extremely slow (only on this system) despite router/laptop restarts etc. Sometimes it just completely disonnects. I ran the wireless script when everything was great for reference and ran it again when it reverted back to the suck. Here are the results for comparison:

Wireless Script Ouput - BAD Connection:
```

*************** info trace ***************

***** uname -a *****

Linux karlFolioMint 3.9.6-030906-generic #201306131535 SMP Thu Jun 13 19:35:54 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    LinuxMint
Description:    Linux Mint 15 Olivia
Release:    15
Codename:    olivia

***** lspci *****

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:17f8]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: wl

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 004 Device 002: ID 125f:312b A-DATA Technology Co., Ltd. Superior S102 Pro
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:2c07 Sunplus Innovation Technology Inc. 
Bus 002 Device 004: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver

***** iwconfig *****

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:252  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


***** rfkill *****

0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

***** lsmod *****

wl                   2573614  0 
lib80211               14352  2 wl,lib80211_crypt_tkip

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth1  [Auto Asus] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Asus:           Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 100 WPA2

  IPv4 Settings:
    Address:         192.168.1.200
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"Asus"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:5/5  Signal level:-2 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDAC0050F204104A0001101044000102103B000103104700107CD8D1061EC1541683CDA9B7B723CDCC102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000752542D4E3636551042001136303A61343A34633A64333A38313A34381054000800060050F20400011011000752542D4E363655100800022008103C0001031049000600372A000120
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s


***** resolv.conf *****

nameserver 127.0.1.1

nameserver 208.67.222.222
nameserver 208.67.220.220

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist brmcsmac
blacklist bcma
blacklist ssb
blacklist b43
blacklist b43legacy
blacklist ndiswrapper
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** dmesg *****

[    4.841863] wl: module license 'unspecified' taints kernel.
[    4.843976] wl: module verification failed: signature and/or required key missing - tainting kernel
[    5.054524] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.112
[ 6808.929447] wlc_print_ampdu_txstatus: txstatus 0x1163
[ 8937.412614] wlc_print_ampdu_txstatus: txstatus 0x3063
[ 8937.412645] wlc_print_ampdu_txstatus: txstatus 0x3063
[ 8937.413115] wlc_print_ampdu_txstatus: txstatus 0xf063
[ 8937.413128] wlc_print_ampdu_txstatus: txstatus 0xf063
[ 8937.413134] wlc_print_ampdu_txstatus: txstatus 0xf063
[ 8937.413139] wlc_print_ampdu_txstatus: txstatus 0xf063

****************** done ******************

```
Wireless Script Ouput - GREAT Connection: 
```

*************** info trace ***************

***** uname -a *****

Linux karlFolioMint 3.9.6-030906-generic #201306131535 SMP Thu Jun 13 19:35:54 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

***** lsb_release *****

Distributor ID:    LinuxMint
Description:    Linux Mint 15 Olivia
Release:    15
Codename:    olivia

***** lspci *****

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168 PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:17f8]
    Kernel driver in use: r8169
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1795]
    Kernel driver in use: wl

***** lsusb *****

Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 1bcf:2c07 Sunplus Innovation Technology Inc. 
Bus 002 Device 003: ID 046d:c521 Logitech, Inc. Cordless Mouse Receiver

***** iwconfig *****

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:250  Noise level:164
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


***** rfkill *****

0: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no

***** lsmod *****

wl                   2573614  0 
lib80211               14352  2 wl,lib80211_crypt_tkip

***** nm-tool *****

NetworkManager Tool

State: connected (global)

- Device: eth1  [Auto Asus] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Asus:           Infra, <MAC address removed>, Freq 2447 MHz, Rate 54 Mb/s, Strength 100 WPA2
    Lighthouse:      Infra, <MAC address removed>, Freq 2412 MHz, Rate 0 Mb/s, Strength 35 WPA WPA2
    NIKAT:           Infra, <MAC address removed>, Freq 2452 MHz, Rate 54 Mb/s, Strength 39 WPA
    GCD-HOME2:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 0 Mb/s, Strength 29 WPA WPA2

  IPv4 Settings:
    Address:         192.168.1.200
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off



***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

***** NetworkManager.conf *****

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

***** interfaces *****

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

***** iwlist *****

eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    ESSID:"Asus"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:5/5  Signal level:-4 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DDAC0050F204104A0001101044000102103B000103104700107CD8D1061EC1541683CDA9B7B723CDCC102100154153555354654B20436F6D707574657220496E632E1023001C57692D46692050726F74656374656420536574757020526F757465721024000752542D4E3636551042001136303A61343A34633A64333A38313A34381054000800060050F20400011011000752542D4E363655100800022008103C0001031049000600372A000120
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
          Cell 02 - Address: <MAC address removed>
                    ESSID:"hpsetup"
                    Mode:Ad-Hoc
                    Frequency=2.437 GHz (Channel 6)
                    Quality:1/5  Signal level:-85 dBm  Noise level:-92 dBm
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
          Cell 03 - Address: <MAC address removed>
                    ESSID:"Lighthouse"
                    Mode:Managed
                    Frequency:2.412 GHz (Channel 1)
                    Quality:1/5  Signal level:-82 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s


***** resolv.conf *****

nameserver 127.0.1.1

nameserver 208.67.222.222
nameserver 208.67.220.220

***** blacklist *****

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist brmcsmac
blacklist bcma
blacklist ssb
blacklist b43
blacklist b43legacy
blacklist ndiswrapper
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

***** dmesg *****

[    4.613038] wl: module license 'unspecified' taints kernel.
[    4.614745] wl: module verification failed: signature and/or required key missing - tainting kernel
[    4.822608] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 5.100.82.112

****************** done ******************

```

ifconfig
```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr b4:99:ba:f7:5e:ec  
          inet6 addr: fe80::b699:baff:fef7:5eec/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:984 errors:0 dropped:0 overruns:0 frame:0
          TX packets:722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1082872 (1.0 MB)  TX bytes:94706 (94.7 KB)

eth1      Link encap:Ethernet  HWaddr c0:18:85:07:b7:fd  
          inet addr:192.168.1.200  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::c218:85ff:fe07:b7fd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2337 errors:0 dropped:0 overruns:0 frame:25373
          TX packets:2080 errors:38 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2102893 (2.1 MB)  TX bytes:237400 (237.4 KB)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:218 errors:0 dropped:0 overruns:0 frame:0
          TX packets:218 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:20231 (20.2 KB)  TX bytes:20231 (20.2 KB)


```

iwconfig
```
$ iwconfig
eth0      no wireless extensions.

eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:248  Noise level:164
          Rx invalid nwid:0  invalid crypt:12  invalid misc:0

lo        no wireless extensions.

karl@karlFolioMint ~ $ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 60:A4:4C:D3:81:48
                    ESSID:"Asus"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:5/5  Signal level:-12 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD310050F204104A0001101044000102104700107CD8D1061EC1541683CDA9B7B723CDCC103C0001031049000600372A000120
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s


```

nm-tool
```
$ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth1  [Auto Asus] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        C0:18:85:07:B7:FD

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Asus:            Infra, 60:A4:4C:D3:81:48, Freq 2447 MHz, Rate 0 Mb/s, Strength 100 WPA2

  IPv4 Settings:
    Address:         192.168.1.200
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        B4:99:BA:F7:5E:EC

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         off


```

iwlist eth1 scan
```
$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 60:A4:4C:D3:81:48
                    ESSID:"Asus"
                    Mode:Managed
                    Frequency:2.447 GHz (Channel 8)
                    Quality:5/5  Signal level:-12 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD310050F204104A0001101044000102104700107CD8D1061EC1541683CDA9B7B723CDCC103C0001031049000600372A000120
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s



```

Any thoughts?

EDIT: I should mention that when I restart, the network is immediately seen with Excellent strenght and the network manager shows "connecting," but after a couple of attempts to connect it fails and then the network shows completely out of range.

---

### Post by varunendra on 2013-06-18
> **kajkob said:**
> You mentioned that building the driver from the source download will be necessary every time the kernel upgrades. The following post mentions locking the version of the driver, would this method be applicable with this solution? [ [http://askubuntu.com/questions/286734/how-to-downgrade-broadcom-wireless-drivers-bcmwl-kernel-source](http://askubuntu.com/questions/286734/how-to-downgrade-broadcom-wireless-drivers-bcmwl-kernel-source) ]
I'm afraid not.
The reason is - unless we can find a patched package in the repositories, the older version is not compatible with 13.04. We can sure pin it, but then it won't compile on it in the first place. Although I have seen at least one post here a few weeks ago someone mentioning that they got a package that worked on 13.04, but I thought it was perhaps a patched package from a third party (something like we are doing here).

> Also, how do I know/tell when the kernel will be upgraded. Is there an obvious designation in the updates that highlights a kernel upgrade?
If you get the Grub menu at startup, its entry for booting into Ubuntu/Mint will change (for example, "Linux with kernel 3.9.6..." instead of 3.9.5). In upgrades, it is listed as "linux-image-<version number>". There is no other obvious notification or indication of kernel upgrade. You can always manually check it with -
```
uname -r
```
You can check all the currently installed kernels with -
```
dpkg --get-selections | grep linux-image
```
*(as an aside, you can uninstall older kernels to recover some disk space (around 100MB per kernel), although it is recommended to keep at least the last working one, so that you can boot with it in case the current one causes problems)*

> Also, if for whatever reason I wanted to undo this process in the future, how would I go about doing so? I noticed previously that using ```
apt-get remove --purge bcmwl-kernel-source
``` did not work after the first time I followed these steps and I tried to reverse them.
Yes, apt-get purge bcmwl-kernel-source won't work because it is not part of installation of that package, we are manually copying the driver. As such, the 'uninstallation' process will also have to be manual, that is -

unload the "wl" driver > delete the copied "wl.ko" module > run "depmod -a" and "update-initramfs -u" again > Un-Blacklist the modules "b43, ssb, brcmsmac and bcma". Everything will be back to defaults again after this (unless you manually did something more that you will need to revert).

> **kajkob said:**
> 
```

iwlist eth1 scan
[CODE]$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: 60:A4:4C:D3:81:48
                    ESSID:"Asus"
                    Mode:Managed
                    Frequency:2.447 GHz (**[COLOR="#FF0000"]Channel 8[/COLOR]**)
                    Quality:5/5  Signal level:-12 dBm  Noise level:-92 dBm
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD310050F204104A0001101044000102104700107CD8D1061EC1541683CDA9B7B723CDCC103C0001031049000600372A000120
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s


```
Any thoughts?.
Try changing the channel from 8 to 1 or 11.

If that does not help, try the native brcmsmac driver instead of the current wl one -
```
sudo modprobe -rfv wl
sudo modprobe -v brcmsmac
```
..and see if it works any better. If it does, we can un-blacklist it and blacklist the wl instead.

---

### Post by kajkob on 2013-06-20
> **varunendra said:**
> 
Try changing the channel from 8 to 1 or 11.

If that does not help, try the native brcmsmac driver instead of the current wl one -


Neither of these worked unfortunately..but new developments have allowed for some progress. There is a new version of the driver being implemented for Ubuntu 13.10 and already available as mentioned in comment #45 on this board [ [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1110139](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1110139) ]. I added that PPA and updated the driver, which allows for the connection to be more stable and the speeds are ok, however, the signal strength is still not great. 

The other problem is that regardless of the driver being used, including the newer 6.30.223.30 linked above, there is a problem with authentication with WPA2 Enterprise networks. There was a post about this somewhere that I lost track of.. This is also a problem for me as I also need to use my laptop at work, so still a work in progress...

---

### Post by varunendra on 2013-06-20
> **kajkob said:**
> There is a new version of the driver being implemented for Ubuntu 13.10 and already available as mentioned in comment #45 on this board [ [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1110139](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1110139) ]. I added that PPA and updated the driver, which allows for the connection to be more stable and the speeds are ok, however, the signal strength is still not great. 
That's an interesting development. I'd wait to see how well it works for others. Obviously, it's going to be the third option in my recommendation list for now, probably first if proves better for others too.

> The other problem is that regardless of the driver being used, including the newer 6.30.223.30 linked above, there is a problem with authentication with WPA2 Enterprise networks.
Is it something about "ca-certificate authentication"? If so, try setting "**system-ca-certs=**" to "**false**" for your connection key-file in /etc/NetworkManager/system-connections. A one-liner to do this -
```
sudo sed -i 's:system-ca-certs=true:system-ca-certs=false:' /etc/NetworkManager/system-connections/*<your connection key-file>*
```
..where *<your connection key-file>* has to be replaced by your connection's key-file name (simply the connection name).

---

### Post by kajkob on 2013-06-20
> **varunendra said:**
> 
..where *<your connection key-file>* has to be replaced by your connection's key-file name (simply the connection name).

As in the SSID?

---

### Post by varunendra on 2013-06-20
> **kajkob said:**
> As in the SSID?

Usually, but not necessarily the same. Just use -
```
ls -1 /etc/NetworkManager/system-connections
```
to make sure.

---

### Post by kajkob on 2013-06-21
> **varunendra said:**
> 
Is it something about "ca-certificate authentication"? If so, try setting "**system-ca-certs=**" to "**false**" for your connection key-file in /etc/NetworkManager/system-connections. A one-liner to do this -
```
sudo sed -i 's:system-ca-certs=true:system-ca-certs=false:' /etc/NetworkManager/system-connections/*<your connection key-file>*
```
..where *<your connection key-file>* has to be replaced by your connection's key-file name (simply the connection name).

Amazing, it works! I spent 40 minutes at the IT help desk in the building and they could not figure out how to connect to the WPA2 Enterprise network on Linux (granted they don't officialy support it). I was given a "this is a known bug with Linux that cannot be overcome at the moment." I just wrote it off as an issue with the driver. Anyway, thanks this is huge progress.. I may be able to boot into Linux exclusively from now on. That is my goal

EDIT: Is there a way to set "**system-ca-certs=**" to **false** permanently? Had to do it again after a reboot..

---

### Post by varunendra on 2013-06-21
> **kajkob said:**
> EDIT: Is there a way to set "**system-ca-certs=**" to **false** permanently? Had to do it again after a reboot..
I thought it WAS permanent :confused:

The keyfile is what tells NetworkManager how to deal with a particular connection and it gets created IF it does not already exist, or only those values get changed that are changed for the connection.

Could you confirm that the value was set to "true" again with -
```
sudo cat /etc/NetworkManager/system-connections/<your key-file> | grep "system-ca"
```
??

If it is getting reset, you may add the command to your **/etc/rc.local** file to do it automatically at every boot. Just make sure to insert any custom line above "**exit 0**" in that file. This is how to do it, but ONLY do it IF the file is indeed getting reset on every boot (which is against what I know about it) -

Open the /etc/rc.local file as root -
```
gksu gedit /etc/rc.local
```

Add the following ling just above the last line "exit 0" -
```
sed -i 's:system-ca-certs=true:system-ca-certs=false:' /etc/NetworkManager/system-connections/*<your connection key-file>*
```
Of course, replace the *<your connection key-file>* with the one you have. Since this file is executed (at every boot) as root, we don't need "sudo" in the command.

It is VERY IMPORTANT that the last line in the /etc/rc.local file should be "exit 0". So insert any custom command always before it.

By the way, good to know it worked :)

---

### Post by kajkob on 2013-06-21
> **varunendra said:**
> I thought it WAS permanent :confused:

The keyfile is what tells NetworkManager how to deal with a particular connection and it gets created IF it does not already exist, or only those values get changed that are changed for the connection.

Could you confirm that the value was set to "true" again with -
```
sudo cat /etc/NetworkManager/system-connections/<your key-file> | grep "system-ca"
```


This command doesn't produce any output, just returns to the default terminal line.. and when I just do ```
sudo cat /etc/NetworkManager/system-connections/<your key-file>
``` to look at the content the line I previously set to 'false' is no longer there..

---

### Post by varunendra on 2013-06-22
> **kajkob said:**
> the line I previously set to 'false' is no longer there..
Did the encryption type change from 'Enterprise' to 'Personal' ? Only the 'WPA Enterprise' and 'Dynamic WEP' need the ca-certificate.

Also, not having that line should have same effect as setting it to "false". Can you still not connect?

You said earlier that you needed to run the command to set it to "false" again after a reboot. Did it help at all the next time?

---

### Post by kajkob on 2013-06-26
After a couple of days of testing, the WiFi behavior on the Enterprise network is unpredictable. Sometimes the WiFi connects immediately on boot/resume and other times the authentication attempt just loops and can never connect, but the network manager sees the network and keeps trying to connect unless I stop it.
> **varunendra said:**
> Did the encryption type change from 'Enterprise' to 'Personal' ? Only the 'WPA Enterprise' and 'Dynamic WEP' need the ca-certificate.
I don't see a line in that file that lists either explicitly, but the file conents don't seem to change wether the connection is successful or not. 

> **varunendra said:**
> Also, not having that line should have same effect as setting it to "false". Can you still not connect?
As mentioned, unreliable/unpredictable.

> **varunendra said:**
> You said earlier that you needed to run the command to set it to "false" again after a reboot. Did it help at all the next time?
Upon the first restart after the initial setting, I had to set to "false" again. Now the line is not there regardless of rebooting, or whether successfully connecting or not.

---

### Post by F00RAX on 2013-09-05
Thanks it worked for me. It's been a long time since I was looking for some help !!!

---

