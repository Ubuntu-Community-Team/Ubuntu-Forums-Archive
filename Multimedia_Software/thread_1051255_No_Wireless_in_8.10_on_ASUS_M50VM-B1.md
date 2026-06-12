---
title: "No Wireless in 8.10 on ASUS M50VM-B1"
date: 2009-01-26
forum: Multimedia Software
---

### Post by ARam1024 on 2009-01-26
I bought a new [Laptop]("http://usa.asus.com/products.aspx?l1=5&l2=132&l3=672&l4=0&model=2383&modelmenu=1") at the beginning of the month, and one of my first projects was putting Kubuntu 8.10 on it.  I first tried the 64bit version, but to my dismay the install froze each time I tried.  Interestingly, this happened with the other distributions I tried too (Fedora 10 [32 bit, 64 bit], openSUSE [64 bit]).

I was able to install Kubuntu 8.10 32 bit.  The install process worked flawlessly, but I was left with two problems.
[LIST]
[*]No sound
[*]No wireless
[/LIST]

I was able to solve the audio problem by looking at [this thread]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/301185").  But that still left the wireless.  I found that the card was from the Atheros AR928X family, so I followed the instructions [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Atheros").  I rebooted and it worked.  I rebooted again, and it didn't work.  Now sometimes it works and sometimes it doesn't.  Any help would be appreciated.

---

### Post by ARam1024 on 2009-02-02
My last post was a little vague about what exactly wasn't working about the wireless.  My card has been recognized from the beginning, but it was unable to find or connect to any wireless networks.  That's the problem I'm still having.

I've been keeping track of this problem, and it seems that if the computer cannot connect to a wireless network at startup, it won't be able to during that session.  I have had times though, where I've put the computer to sleep, changed locations (home to school), and the wireless worked perfectly.

Also, it seems that my installation isn't entirely stable.  It's a gamble whether Kubuntu will start properly when I reboot.  Sometimes the bootup process will print out something like "expected type X found type C" and start "reading files needed to boot".  After that happens, Kubuntu works ok (excluding wireless).  Sometimes though, my laptop will emit a loud continuous tone when trying to boot into Kubuntu.  Sometimes it continues the boot process.  Sometimes it doesn't.

Any help would be appreciated.  If anyone wants more information, I'd be happy to give it.

Thanks,
ARam1024

---

### Post by ARam1024 on 2009-02-04
I found a fairly strange workaround for this wireless problem.  If I put the computer to sleep and then wake it up immediately wireless works.  Since this isn't really a solution, I posted this bug to [launchpad]("https://bugs.launchpad.net/ubuntu/+bug/325535").

---

### Post by ARam1024 on 2009-02-10
I found a forum post about trouble installing 64 bit versions of Ubuntu and Fedora, so maybe I'll be able to work something out [there]("http://forums.fedoraforum.org/showthread.php?t=208639").

---

### Post by ARam1024 on 2009-02-11
I just found a thread on the same subject.  You can follow it [here]("http://ubuntuforums.org/showthread.php?p=6718958#post6718958").

---

### Post by ARam1024 on 2009-02-11
I think I've managed to completely fix the wireless problem.  I found another post [here]("http://ubuntuforums.org/showthread.php?t=921556&highlight=ASUS+M50VM") that said to delete /etc/acpi/start.d/60-asus-wireless-led.sh.  I did that, and my wireless has been working.  I'll post again if something else happens.

---

### Post by SketchyClown on 2009-02-12
Probably you have a similar BIOS to my M50VM-A1.

The issue with the CD/DVD drive failing during installs was in my BIOS.

Yeah I got it to work once or twice fully, but mostly it stalled out during installation.

And burning CD/DVD's was near impossible.

Found a solution that if you set the option on the drive in the BIOS from "Enhanced" to "Compatible"the drive works as it should.

No more stalling out.

I also have the AR928x wireless and it is supported in 8.10, but I found as you that it would work, but either drop off or not connect.

This might sound odd but I did a re-installation of Intrepid 8.10 and made sure that I had a ethernet cable connected to the laptop so that the installer is able to **'configure the network with DHCP'** during installation. I had been skipping this step due to the fact that the default repository that it sets me to is like on dial-up and makes a fast installation extremely slow when configuring APT during installation.

So I let it do its thing, and when it was finished my wireless was connecting and staying connected this time. Except it would still dump after like 12hrs of being connected.

So now I have edited this file, as **'sudo' **of course:

**/sys/devices/platform/asus-laptop/wlan **and set the value to '1' from '0', to see if this will keep the wireless always on, since the '0' value seems to be a value to auto-manage some devices. 

Hope this helps you too.

---

### Post by ARam1024 on 2009-02-23
@SketchyClown
Thanks for your response.  When I'm installing other OSs (Fedora 10 64 bit), it seems to work fine now.  However, when I try to get back into Windows, I get blue-screened until I turn the setting back to "Enhanced".  I'll do more research on it when I get time.

@all
Recently I've found that after waking my computer up, it refuses to connect to networks.  I found another copy of the 60-asus-wireless-led.sh script in /etc/acpi/resume.d, and I deleted it. I'll post on how the situation progresses.

---

### Post by troegs on 2009-02-24
Hey ARam. I had quite a bit of trouble putting ubuntu on my g50vt. As I've just got done saying in several other posts, (all by Asus owner interestingly) that all my install hangs with intrepid were solved by burning the cd at the slowest rate possible. Sounds like crap I know but there is some real computer geek reasoning behind it that I'll spare you. In any event give it a show if you ever give intrepid a try again in the future. 

One other thing I wanted to say as well, though it is true that you have to set your HD to compatability mode when installing your linux OS, once it's installed you should not, at all, ever, (sorry but I've been up for almost 48 hours and this is the best I can do at adding emphasis) have to switch back and fourth anymore. You should be able to leave it in enhanced mode permanently. If you can't then, sadly I hate to tell you, you may need to give it another go at an install, (with a disk that was burned at half a snail's pace if possible). Hope you get that drive setting issue worked out, and you're just gonna have to trust me on the slow burn thing. It's an issue I'm seeing all over the place with intrepid by Asus users, as well as a few others. I'm thinking about just making a text file with a stock post about it. 

Anyhow, good luck and hope some of this helps steer you in the right direction.

---

### Post by k.sanjith on 2009-04-29
Try Reloading the module ASUS_LAPTOP(in 8.10).
After doing this I was able to detect and connect to wireless networks on my ASUS laptop.

---

