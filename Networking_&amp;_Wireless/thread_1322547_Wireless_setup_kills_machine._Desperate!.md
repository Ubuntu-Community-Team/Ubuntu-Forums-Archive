---
title: "Wireless setup kills machine. Desperate!"
date: 2009-11-11
forum: Networking &amp; Wireless
---

### Post by Bucky Ball on 2009-11-11
Hi all, 

Long story short: Wireless card died on my machine so just bought an OpenNetworks iConnect i306. Plugged it in and see wireless network straight away and is giving me 92% signal! Excellent. But not connecting to the internet. Odd.

So I begin to tweak and realise it has allocated itself as wlan1. My setup seems to be looking for wlan0.

So I tried this:

```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> up
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> key HEX_KEY <<<-------- If using ASCII Equivalent, this is s:ASCII_KEY (please make note of the prefix s:)
****Additional Comand that may be needed  -- sudo iwconfig <interface> key open  <<<----See note below
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>
```Where <interface> = wlan1, from this page:

[http://ubuntuforums.org/showthread.php?t=684495](http://ubuntuforums.org/showthread.php?t=684495)

I realised this was for DHCP and I am running static ips on our three machines so I went for the static setup, changing the IPs where appropriate:

```
sudo ifconfig <interface> down
sudo dhclient -r <interface>
sudo ifconfig <interface> 192.168.1.100 netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1
sudo iwconfig <interface> essid "ESSID_IN_QUOTES"
sudo iwconfig <interface> mode Managed
sudo dhclient <interface>

```Not much change. wlan1 buzzing along with great signal but think the machine is looking for wlan0.

So I notice the USB wireless dongle has Linux drivers on the install CD. I have a choice of a folder called Debian31 or Linux26x. I go for the latter.
In the folder is a README file so I follow the instructions in there:
 [LEFT]
> [LEFT]// Build source code and insert modules.[/LEFT]
    //-----------------------------------------------------------------------------
    [LEFT]1. Unpack source code:[/LEFT]
    [LEFT]    tar -zxvf stack.tar.gz[/LEFT]
    [LEFT]    tar -zxvf drv.tar.gz[/LEFT]
    
    [LEFT]2. Build and insert modules:[/LEFT]
    [LEFT]    cd ieee80211/[/LEFT]
    [LEFT]    **make clean;make**[/LEFT]
    [LEFT]    insmod ieee80211_crypt.ko[/LEFT]
    [LEFT]    insmod ieee80211_crypt_wep.ko[/LEFT]
    [LEFT]    insmod ieee80211_crypt_tkip.ko[/LEFT]
    [LEFT]    insmod ieee80211_crypt_ccmp.ko[/LEFT]
    [LEFT]    insmod ieee80211-r8180.ko[/LEFT]
    [LEFT]    cd -[/LEFT]
    [LEFT]    cd beta-8187/[/LEFT]
    [LEFT]    make clean;make[/LEFT]
    [LEFT]    insmod r8187.ko[/LEFT]
[/LEFT]

All went well until step 2 and the command I have in bold. I had never seen that command before but it wouldn't run anyway so I changed it to:

```
make clean
```That may have been the dumbest thing I could have done because now I can't even get into the machine. Windows boots fine, Live CD and Live Gparted work fine so forget hardware issues when I tell you this: I boot into the regular kernel and proceedings cease and the progress bar stops sliding and the caps lock light flashes on and off; I boot into the recovery kernel and it halts with these three lines:

```
Begin: Running /scripts/init-bottom ...
Done.
run-init: /sbin/init: no such file or directory
kernel panic - not syncing: Attempted to kill init!
```End of story. That is it. No progress from there.

I would hunt for a few days before posting here but I am in the last week of uni with a bundle of work to tie up and need to get onto this machine and online pronto to get some things. I managed to retrieve my files using the Live CD but I use Zotero for referencing which sits on Firefox. Can't boot the machine so can't get to Firefox/Zotero/References. If anyone knows where Zotero stores these files would be a great help as I have two almost complete assignments with no bibliographies. 

Desperate and hope someone can HELP!! ;-)

* PS: once the laptop stops at boot there is no way of getting in; ctl/alt/backspace, F*, nothing works. The only thing to is hold down the power button and switch off. AAGH! Why now??? But ain't that the way ...

---

### Post by Bucky Ball on 2009-11-11
Well, I managed to get online booting from a Live CD but having no luck. Can't see anything odd in there. It took nine or ten hours but I eventually managed to retrieve the stuff I needed for uni and set it up as it was on another machine. Phew. Nightmare. But I can get online and into the machine this way so if anyone has any ideas, fire away ... please! ;-)

I am going to have to leave the laptop situation for a few days but if anyone has any ideas on how to fix the kernel panic ... can someone tell me how to reinstall the kernel? I have been hunting for how to do that but not finding much. Thought it might be a kernel upgrade but how do it from a live CD?

One odd thing; the second time I booted into the Live CD, it offered me drivers for the internal wireless card which died about a month and a half ago and hasn't been seen since. That's the reason I bought the USB wireless dongle and got into this mess! I looked in Hardware Drivers and there was the appropriate driver waiting to be enabled. Opened a terminal and ran 'lspci' and there it was, the long lost Broadcom card! I tried enabling the B43 driver, got an error at the end of installing fw-cutter and that was it. The driver did show as enabled but no go with the card. Driver vanished on re-boot. 

Weird s**t, fascinating and all but bad timing for me. 

Any and all ideas appreciated. I will try a few things over the weekend if I have any time. :)

---

### Post by Bucky Ball on 2009-11-14
Anyone?

---

