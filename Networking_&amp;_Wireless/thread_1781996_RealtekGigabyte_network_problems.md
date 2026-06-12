---
title: "Realtek/Gigabyte network problems"
date: 2011-06-14
forum: Networking &amp; Wireless
---

### Post by mombooks on 2011-06-14
Hi All,

I've a gigabyte 890GPA-UD3H motherboard here with an embedded realtek 8168B network card. Running 11.04 I've read that there are problems with the drivers for this model of network card and I'm having terrible issues.

Network worked fine with the Live CD during the initial install, using DHCP (automatic background connection), but as soon as the system was installed I had no network access.

Having read a few related posts here, I downloaded the latest drivers:
[http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D(L)%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8168E](http://www.realtek.com/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D(L)%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8168E)

which seem to have installed successfully, but I'm still having no luck- the lights on the ethernet port are not lighting up (although one green one flashes if i plug in to eth2 on my mac, which shares it's network connection), and my network connection set up through the gui says 'last used - never' I tried setting network as dhcp in /etc/resolv.conf but it doesn't want to work.

Now I've gone to reinstall ubuntu from the same disk, and the installer can't connect to the internet - booted from disk - it's connected to the same LAN port in my office- have tried 2 others - is this because the drivers changed after the install?

Any advice would be hugely appreciated.

---

### Post by ratcheer on 2011-06-14
You can look at the thread I had a few days ago. What driver is your card supposed to use?

[http://ubuntuforums.org/showthread.php?t=1778702](http://ubuntuforums.org/showthread.php?t=1778702)

And, yes, I had to reinstall Ubuntu yesterday and mine wouldn't connect to the internet, either. It did not act that way during my original installation.

Tim

---

### Post by mombooks on 2011-06-14
glad to hear it's not just me! Where can I find the bugs referenced by their numbers in your thread?

the install of the driver seemed to go OK for me (no errors during install), it just doesn't work..

Also, my directory holding the driver had no spaces in it originally (r8168-8.024.00) which is the driver my card should be using.

Could anyone recommend a cheap network card that is known to work well with ubuntu? Preferably with good drivers included in the base install...

---

### Post by ratcheer on 2011-06-14
Now that you have installed the correct driver, do the following to get Ubuntu to actually use it:

sudo depmod -a

Edit /etc/modprobe.d/blacklist.conf and add a new line with "blacklist r8169"

Edit /etc/initramfs-toold/modules and add a new line with "r8168"

Run "sudo update-initramfs -v -u -k `uname -r`

Reboot

Run "sudo lspci -v" to verify that the new driver is loaded.

As to the bug reports on launchpad.net, there are really too many to try to list. Do a search on r8169 and you will see tham too. One that seemed very similar to me was 770708.

The NIC is not the problem, the problem is that Ubuntu is choosing an incorrect driver. With the correct driver installed, my NIC is doing just fine. Oddly, just morning I had to do exactly the same thing to get Ubuntu to use my Ralink wireless card.

Tim

---

### Post by mombooks on 2011-06-14
Thanks for helping out! I've run the steps you've recommended, to limited avail - when i run lspci it says
Kernel driver in use: r8169
Kernel modules: r8168

I think I may have messed up the Run "sudo update-initramfs -v -u -k `uname -r` part, i ran
"sudo update-initramfs -v -u -k `uname -r`" and the feedback included lots of module not found FATAL errors - have i entered the command incorrectly?

---

### Post by mombooks on 2011-06-15
UPDATE: This morning the thing works fine, and lspci outputs 

Kernel Driver: r8168

no idea why now though! I restarted multiple times yesterday - the only thing I can think is that this morning I installed a graphics card and am using that instead of the onboard graphics, which meant that the first time I started up with it installed, it ran GNOME instead of Unity as the drivers weren't yet installed.

Weird.

Thanks again for your help Tim!

---

### Post by ratcheer on 2011-06-15
Probably the reason it didn't work yesterday is that the marks enclosong uname -r are grave accents, not quotation marks. It is usually the key to the left of the numeric 1 key. What it meand is to interpret the enclosed command and use the result. I should have mentioned that in my post.

Anyway, I'm glad things are working for you, now.

Tim

---

### Post by rs321 on 2011-06-15
My network is not recognized so I can't enter a string of code.  Should I blow-away ubuntu and hope it works better next time?

---

