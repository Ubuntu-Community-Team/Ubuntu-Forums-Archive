---
title: "Ubuntu 12.10 vs. BootMed"
date: 2013-01-24
forum: Networking &amp; Wireless
---

### Post by Dennis1 on 2013-01-24
Caveat: I'm a newbie to ubuntu and am running the Live CD's for Bootmed and ubuntu 12.10
 
I can browse my work network with Bootmed's ubuntu flavor and, when prompted for my network credentials, can provide them and access network folders. When I try to do the same thing with ubuntu 12.10 (32-bit), it will not accept my credentials. I get the same thing with ubuntu 12.10 (64-bit), but I get an additional failure to mount resources initially so I'm focusing on just getting 32-bit to work for now.
 
I looked at the network settings for Bootmed, which defaults to the following:
Connection Name = Auto eth0 // "Connect Automatically" is checked // "Available to all users" is checked
Wired tab: MTU = automatic
802.1x Security tab: Use 802.1x security is unchecked
IPv4 Settings tab: Method: Automatic (DHCP) & "Require IPv4 addressing" is checked
IPv6 tab: Method: Ignore
 
When I look at the network settings for ubuntu 12.10 (32-bit), I make the following changes to try to mimick Bootmed with the following results:
 
After changing the connection name and changing IPv6 to Ignore, I get an error "Sorry, Ubuntu 12.10 has experienced an internal error.
Details:
ExecutablePath:
/usr/bin/nm-connection-editor
Package
network-manager-gnome 0.9.6.2-Oubuntu6
ProblemType
crash
Title
nm-connection-editor crashed with SIGSEGV in g_type_instance_get_private()
ApportVersion
2.6.1-Oubuntu3
Architecture
i386
 
This is all being done from Live-DVD's on an HP Elitebook 8770w with 8GB of RAM and a 500GB drive, which normally boots to Win7 x64. Perhaps the BootMed image simply has the necessary drivers, but I can see the folders in both ubuntu distros - I just can't get my credentials to work for ubuntu 12.10. I'm guessing that since ubuntu is loaded into RAM that the write-back update should change values in RAM and not actually try to write back to the DVD-R disk, which could never be updated. 
 
Our DNS servers don't support IPv6 so I thought perhaps this may be the issue and hoped to be able to easily diable IPv6. It's not critical to get this working, but if it's a simple config change, then I'd love to understand it to encourage me to work more with ubuntu. It has been decades since I worked in UNIX and it's nice to get away from Windose ... even if for a little while :)
 
Thanks for the help !!!

---

### Post by praseodym on 2013-01-24
Hi,

what hardware is in use? Do you want to install later or using the LIVE-DVDs permanently? Please check in a terminal (CTRL+ALT+T) the outputs of:
```

lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
```
For deactivating IPv6 go to the network-manager-applet->IPv6-settings and "ignore".

---

### Post by Dennis1 on 2013-01-24
Wow, that's the quickest reply in a forum that I've ever received - Thank You !!
 
This is a work machine that will, regretfully, never have Linux loaded permanently.  I have used the BootMed Live-DVD on a couple of laptops and a PC and I've been amazed that I can connect to our network.  I used it for a machine that couldn't reboot (parition table got fouled up) to save all of the data on the hard drive by uploading it to a network drive - It was a beautiful moment ...
 
I've tried the ubuntu Live-DVD on different machines and it never lets me connect to our network with my credentials.  I can see the network shares, but when I enter my credentials, it pops up the screen again to re-enter them, eventually locking out my account.
 
I actually just recovered this machine in question (SecureDoc encryption fried it so it wouldn't reboot, but I was able to use the Win 7 x64 DVD to restore it so it would boot back up using "bcdboot c:\Windows" ...
 
I was hoping it was a general comparison type of question than particular drivers missing for a particular hardware configuration since it seems to act the same on different devices.  It sounds like the steps I took to deactivate IPv6 match your suggestion.  I launched Network settings from GUI (No sudo so I'm hoping it considered me to be a Super User/Admin) --> Clicked "Options," then clicked on IPv6 tab and set it to "Ignore" - Although I got the error I described, when I went back into it, it appeared to retain the setting so it sounds like that was successful.  Still, no joy after making the change ...
 
Thanks again for the insight - I really love the ubuntu interface as the most intuitive one I've seen in my recent shallow step into the Linux pool.

---

### Post by Dennis1 on 2013-01-25
I can't launch ubuntu from the original laptop since I'm in the middle of encryption, but I did launch ubuntu 12.10 (32-bit) from yet another laptop (HP Elitebook 8440p) and captured the info that you requested.  Again, I was able to see the shares, but couldn't access them with my network credentials.
 
- I'll have to Google to see if there is an equivalent for Ctrl-C and Ctrl-V in ubuntu :) ...
 
Please check in a terminal (CTRL+ALT+T) the outputs of:
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
 
After verifying the same issue happens on this different laptop, here is the captured data as requested (Attached files by name of terminal command)

---

### Post by Dennis1 on 2013-01-25
- Had the same thing happen on this HP 8470p as well
 
Please check in a terminal (CTRL+ALT+T) the outputs of:
lspci -nnk
lsusb
lsmod
iwconfig
rfkill list
 
After verifying the same issue happens on this laptop, here is the captured data from this machine (Uploaded files named after commands).

---

### Post by Dennis1 on 2013-01-25
I'm going to have to stop doing so much testing with this at work ... People are starting to ask why my account keeps getting locked out (We can't unlock ourselves) ...  At any rate, I seem to always connect to our network with Bootmed's 32-bit release just by booting up on a wide variety of laptops and PC's, but can never seem to do the same with ubuntu 12.10 (32-bit).  
 
Clearly, there is a difference in network settings between BootMed's flavor of ubuntu and the "standard" release of ubuntu 12.10.  Perhaps they'll work out those differences in the next major release.  Thanks for educating me on several commands for network discovery in ubuntu, not to mention leading me into working with the terminal and some "Office" type apps.  I really do like the ubuntu interface.
 
:popcorn:
 
I'll get the specs on the original laptop in case there is a pattern ...

---

### Post by Dennis1 on 2013-01-25
Here is the data from the original HP 8770w

---

### Post by praseodym on 2013-01-25
For the original one, deactivate the N-mode of the driver (bug):
```

echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
```
This is not permanent, you can type it in every boot-up.

---

### Post by Dennis1 on 2013-01-25
Thanks for walking me through this with all of the code.  I've forgotten so much from my UNIX days ...  
 
I'm reloating Win7 x64 on the HP 8770w laptop now due to it having 2 devices with the larger 500GB drive as device 0 and the 200GB drive as device 1 and the encryption only looks at device 0 and I'm not taking the laptop apart to change where the hard drives plug into the mobo ...
 
Anywho, does it look like the same problem exists on either of the other two laptops, which I have access to test now without waiting on Win 7 to install ...
 
Also, thanks for the note letting me know that everything is being written into RAM and not the hard drive since these are work machines and I can't mess them up.  Your kindness to newbies doesn't go unnoticed ;) ...

---

### Post by praseodym on 2013-01-25
Yes, its the same module on the other laptop. If you cant write to disk, the module parameter can be applied directly "live":
```

sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi 11n_diable=1
```

---

### Post by Dennis1 on 2013-01-28
I got back on the original HP EliteBook 8770w and deactivated the N-mode of the driver on the original laptop with:
Launched Terminal (CTRL+ALT+T), then entered the following lines:
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi
 
- The first time I entered the 2nd line (/etc/modprobe.d/iwlwifi.conf) I got a bash: /etc IS a directory (or something to that effect)
- The first time I entered the 3rd line (sudo modprobe -rfv iwlwifi) the command was followed up by:
remove (/sbin/lsmod ... etc); rmod /lib ...; rmod /lib/modules ...
- The 2nd time I entered the 2nd line, I got:
bash: /etc/modprobe.d/iwlwifi.conf: Permission denied
 
Soooo, I tried the following two commands
sudo modprobe -rfv iwlwifi
sudo modprobe -v iwlwifi 11n_disable=1 (added the "s" to disable)
 
Got the same results, i.e. keep getting prompted for my credentials, but never actually can access the network shares via the Ethernet connection.  Are these commands for Wifi or Ethernet?
 
I'm running the LiveDVD and do NOT have ubuntu installed on the hard drive.  Thanks again for all of the great help, complete with code !!

---

### Post by praseodym on 2013-01-28
```
 echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf
```
This is one line, you better c/p it!

---

### Post by Dennis1 on 2013-01-29
Praseodym - I booted to the ubuntu 32-bit disk, launched Terminal (CTRL+ALT+T), then opened Firefox, which connected fine through our network and to the Internet, navigated to this thread and copied the following commands from your initial post:
 
Copy and pasted:
echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf and pressed <enter>
 
The following appears after entering this command:
options iwlwifi 11n_disable=1
 
Copy and pasted:
sudo modprobe -rfv iwlwifi and pressed <enter>
 
The following appears after entering this command:
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 
rmmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko 
rmmod /lib/modules/3.5.0-17-generic/kernel/net/wireless/cfg80211.ko
 
Copy and pasted:
sudo modprobe -v iwlwifi and pressed <enter> 
The following appears after entering this command:
insmod /lib/modules/3.5.0-17-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable=1
 
Tried logging in twice (hopefully didn't lock my account again) and keep getting prompted for network credentials ...

---

### Post by praseodym on 2013-01-29
What does the file look like now?

```
cat /etc/modprobe.d/iwlwifi.conf
```

---

### Post by Dennis1 on 2013-01-30
Here you can see the file BEFORE issuing the commands and AFTER issuing the commands:
 
ubuntu@ubuntu:~$ cat /etc/modprobe.d/iwlwifi.conf 
# /etc/modprobe.d/iwlwifi.conf 
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the 
# microcode file installed on the system. When removing iwlwifi, first 
# remove the iwl?vm module and then iwlwifi. 
remove iwlwifi \ 
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \ 
&& /sbin/modprobe -r mac80211 
ubuntu@ubuntu:~$ echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf 
options iwlwifi 11n_disable=1 
ubuntu@ubuntu:~$ sudo modprobe -rfv iwlwifi 
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 
rmmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko 
rmmod /lib/modules/3.5.0-17-generic/kernel/net/wireless/cfg80211.ko 
ubuntu@ubuntu:~$ sudo modprobe -v iwlwifi 
insmod /lib/modules/3.5.0-17-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable=1 
ubuntu@ubuntu:~$ cat /etc/modprobe.d/iwlwifi.conf 
options iwlwifi 11n_disable=1 
ubuntu@ubuntu:~$ ^C 
 
lol ... I keep trying to Ctrl-C to copy ... Can't help myself :)

---

### Post by Dennis1 on 2013-02-04
):p

---

### Post by Dennis1 on 2013-02-05
:popcorn:

---

### Post by Dennis1 on 2013-02-06
ubuntu@ubuntu:~$ cat /etc/modprobe.d/iwlwifi.conf 
# /etc/modprobe.d/iwlwifi.conf 
# iwlwifi will dyamically load either iwldvm or iwlmvm depending on the 
# microcode file installed on the system. When removing iwlwifi, first 
# remove the iwl?vm module and then iwlwifi. 
remove iwlwifi \ 
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \ 
&& /sbin/modprobe -r mac80211 
ubuntu@ubuntu:~$ echo "options iwlwifi 11n_disable=1" | sudo tee /etc/modprobe.d/iwlwifi.conf 
options iwlwifi 11n_disable=1 
ubuntu@ubuntu:~$ sudo modprobe -rfv iwlwifi 
rmmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 
rmmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko 
rmmod /lib/modules/3.5.0-17-generic/kernel/net/wireless/cfg80211.ko 
ubuntu@ubuntu:~$ sudo modprobe -v iwlwifi 
insmod /lib/modules/3.5.0-17-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.5.0-17-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko 11n_disable=1 
ubuntu@ubuntu:~$ cat /etc/modprobe.d/iwlwifi.conf 
options iwlwifi 11n_disable=1

---

### Post by Dennis1 on 2013-02-13
I found out that, apparently, Ubuntu tries to authenticate to the network automatically and subsequently fails.  This was learned when one of our network engineers started yelling around asking if anyone was running Ubuntu as he had attempts at network authentication and I was the only one running Ubuntu and was NOT trying to access a server with my credentials  :oops:

---

### Post by Dennis1 on 2013-03-08
Any idea when the next version of Ubuntu will be released and if it will possibly address this issue?  I'm hangin' in there :) ...

---

### Post by praseodym on 2013-03-08
Have you tried 13.04 (which is still alpha) per Live-CD/USB?

---

