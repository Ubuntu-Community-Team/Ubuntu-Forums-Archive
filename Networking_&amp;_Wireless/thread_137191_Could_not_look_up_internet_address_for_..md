---
title: "Could not look up internet address for ."
date: 2006-02-27
forum: Networking &amp; Wireless
---

### Post by sdb2028 on 2006-02-27
I have been having problems with ubuntu connecting to the internet for some time. Just when I think the problem iis solved, it starts up again. Usually works fine all day (once I finally get it connected), however when I shut down the computer at night I have to fight with it for an hour or so to get it back on. I have list of things I go through (checking iwconfig, ifconfig, System-Admin-networking-wireless-config etc). After a while it comes up.??? Don't really know which tail chasing job got it going. Now I have a NEW problem. My networking comes up on boot, I can acceess the internet, but I get this error which says- Could not look up internet address for . (then something about Gnome won't work right) and I can fix it by adding it to /etc/hosts. I have looked---- there is no such file..??
I figure I must have done something incredibly wrong while looking through the install file for upgrading my wireless drivers and firmware. It is an Intel Pro/Wireless 2200. I didn't do though upgrades yet, I was following along with the directions and found that a lot of the files it was describing did not exist.
I am online with my wireless right now, don't know how long it will last, but I cannot access my networking control panel in System-Admin.
Anybody out there have a clue as to what I may have screwed up?:-k

---

### Post by claes on 2006-02-27
It could be that the machine can't resolve it's own hostname so you should recreat the /etc/hosts file. Here is mine:

127.0.0.1 localhost.localdomain localhost tdselt0136  <-- change to your name

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

---

### Post by sdb2028 on 2006-02-27
To make sure I do this correctly (without "screwing" something else up)-
Do in terminal:
sudo gedit /etc/hosts

then enter:
"127.0.0.1 localhost.localdomain localhost"    [tdselt0136] <-- change to your name

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts

(all of the above exactly as written) then save??


P.S. I am using a linksys wireless G router and have ipv6 off in modprobe.d/aliases

---

### Post by claes on 2006-02-27
Yep and instead of tdselt0136 you write your own hostname. You can see that by using the hostname command.

Claes

---

### Post by sdb2028 on 2006-02-27
OK, more problems- heres what happens:
steve@:~$ sudo gedit /etc/hosts
sudo: unable to lookup  via gethostbyname()
steve@:~$

and what happened to my prompt? something is missing!

---

### Post by claes on 2006-02-27
That is also for that /etc/hosts file is missing. hmmm might need to think for awhile how to fix this. Try to use a text based editor instead of gedit. If it's the $DISPLAY variable that spooks when the machine is not able to resolv it's own name.

Claes

---

### Post by sdb2028 on 2006-02-27
Thanks for your help, I'll be waiting patiently.

How do I use the text editor if it won't let me save when not in root?

---

### Post by claes on 2006-02-27
Well that's the problem it wont let you. So you have to be root with sudo and sudo don't work the machine can't resolv its own name. You might notice this is a moment 22. So you have to edit start the machine in runlevel 1 to be root. The easiest way to do this is to use: sudo init 1 but sudo won't let you. So the more complicated way to do this is to tell grub to boot up in runlevel 1. And that have to done from grub. Meaning that you have to reboot your machine. When grub apears and counting down you press esc and then you can see a bout up menu. You choose the top one, and press e for edit then you will se to lines one starting with kernel and the other start with initrd. You choose the line starting with kernel and press e for edit again. Then you will be able to edit the line. And the very end of that line you write 1 nothing else just the number 1. and then you hit enter and then b for boot. The machine will then boot to runlevel 1. You should se a prompt and there you should be root. Try whoami and see that you are root. Then you could create the /etc/hosts file. And then reboot your machine with shutdown -r now. The machine will be back online and beeing able to resolv it own hostname. 

The grub fiddling will not change anything in the grub config file on the disk. So if you get something wrong just reboot and everything is back as normal.

Claes

---

### Post by sdb2028 on 2006-02-27
Thanks, here it goes!
I'll be back in a little bit, tell you how it went. (I hope)

---

### Post by claes on 2006-02-27
Good luck.

Claes

---

### Post by soonindallas on 2006-02-27
to create such a file here are the steps using nano the text based editor.

you may be able to do this in a terminal without rebooting.  but if your display is the problem you may have to reboot.

- print out or copy the text you want on a piece of paper
- boot and choose recovery (text console) mode
- login; you are root
- type ```
nano /etc/hosts
```
- enter the text you wrote down
- follow the instructions to save and quit (from memory it's ctrl-x to quit, confirm the file name, then 'y' but the commands are clear on the bottom of the screen)
- reboot as normal and see if it solved your problem

---

### Post by claes on 2006-02-27
But now the problem was that sudo don't work when it can't resolv the machines name. And that's probably the hardest thing to fix. But the rest is good. Didn't think about telling him about nano hope he will find an text editor. Another way is to save the file in $HOME and then copy it in place. But still have to do it in runlevel 1.

Claes

---

### Post by soonindallas on 2006-02-27
ok.  just realised I wrote a bunch of crap cos when you log in in recovery mode you are root so no need for sudo.

could also boot from a live CD and copy the file over to the root partition after mounting it.  that's probably what you should do steve.

can you DL a live CD image and burn it ?

---

### Post by claes on 2006-02-27
Why burn a cd when all you need is to tell grub to boot in runlevel 1? Or even rescue mode. If that logs you in as root without a root password? Never tried rescue mode so I don't know.

Claes

---

### Post by sdb2028 on 2006-02-27
Well, I back.... unfortunatly am going through Windows. I try'd adding the "1" to the end of the kernel line...... it locked up on boot. I had to turn the computer off to reboot and.. well now I cant get into my network setting to get it to access the internet. I think I will have to try a fresh install and start over (again) unless you have any more ideas.
Thanks again for your help.
Steve

---

### Post by claes on 2006-02-27
If you try the rescue mode and create the /etc/hosts file. If that is in place the rest should be easier.

Claes

---

### Post by sdb2028 on 2006-02-27
OK, I went through rescue mode, got the file edited. Still has the same problem. Also found a file named "hostname" which is empty.
got another step?

---

### Post by sdb2028 on 2006-02-27
OK, thanks for al your help guy's, I finally just went did a fresh install. now I'm back online. 
However, does anyone know why the network configuration won't seem to start properly after powering down the computer? I have a Toshiba Satellite M45 which I have set up to dual boot with WinXP. The network works just fine in Windows, and works fine in ubuntu, even after reboot- as long as I don't physically turn the power off.
?????????????? strange??????????

---

### Post by sdb2028 on 2006-02-28
Well back to the same ole @##%.
Not working again, connects about every twenty'th time. Getting very frustrating.
Need a real magitian for this one, there seems to be a whole lot of people with this problem.
If anyone comes up with a perminent fix, please pass it on.

---

### Post by sdb2028 on 2006-02-28
bad spelling, meant to say "Need a real Magician"

---

