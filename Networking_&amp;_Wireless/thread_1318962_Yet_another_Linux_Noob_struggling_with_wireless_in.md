---
title: "Yet another Linux Noob struggling with wireless internet"
date: 2009-11-08
forum: Networking &amp; Wireless
---

### Post by goodlukeing on 2009-11-08
I have converted to linux for the first time 2 days ago (thanks to wubi), I don't get much of this as of yet, but I'm willing to learn. Basically when I log on to windows my wireless works fine, but when I go onto ubuntu it says its fine but it goes through phases of just doing "loading" with a blank screen and then quickly loads a page.

I searched (ok i'll admit it, briefly) for solutions to this problem and it appears many people have gotten it with this ubuntu 9.10. I tried their solutions which mainly include typing sudo followed by something I do not understand at all into the terminal but usually that gets errors. Some people installed a driver, I don't  know what mine is, how do I find out, is it on the back of the modem thing or is it some wireless thing within my computer, I don't know any of this stuff. All I know is that the blue bars in the corner say I'm 100% connected but I go through phases of connection on mozilla.

Does anyone know how to help me, hopefully in words I'll understand. I just don't want to go back to windows, I don't find paying for a virus-infected operating system that struggles to open my computer in a reasonable length of time worthwhile.

---

### Post by greatn on 2009-11-08
At a certain point I don't think you have to blame yourself for being a noob, I think you have to blame Canonical. I plug in Windows Vista, it works, I have wireless. I plug in OS X, it works, I have wireless. I plug in Ubuntu 9.10, I need to go to terminal, type a bunch of stuff in I don't understand, download some files, do a bunch of trial and error, and still not have anything work.

I'd still like to use Ubuntu because I like the interface, and because it is fast, but past a certain point I think it is fair to say Canonical is the problem, not the end users.

---

### Post by t0mppa on 2009-11-08
> **goodlukeing said:**
> I tried their solutions which mainly include typing sudo followed by something I do not understand at all into the terminal but usually that gets errors.

Ok, just a bit of advice: never ever use sudo and some command you don't understand, you could end up breaking your whole installation and/or lose a lot of valuable data like that. If you don't understand, ask first or find out (you can use **man <command>** on terminal to get a manual of sorts about what the command does and how it works or just ask Google) yourself.

> **goodlukeing said:**
> Some people installed a driver, I don't  know what mine is, how do I find out, is it on the back of the modem thing or is it some wireless thing within my computer, I don't know any of this stuff.

You can find which chip your wireless card is using and which driver is being associated with it by running **lshw -C network** from the terminal. Both can be important details for troubleshooting.

> **goodlukeing said:**
> All I know is that the blue bars in the corner say I'm 100% connected but I go through phases of connection on mozilla.

Ok, how often do you face these phases and how long are they? Can you still ping (for instance **ping -c 4 [www.google.com](www.google.com)**, to ping Google with four packets) sites during them?

---

### Post by t0mppa on 2009-11-08
> **greatn said:**
> At a certain point I don't think you have to blame yourself for being a noob, I think you have to blame Canonical. I plug in Windows Vista, it works, I have wireless. I plug in OS X, it works, I have wireless. I plug in Ubuntu 9.10, I need to go to terminal, type a bunch of stuff in I don't understand, download some files, do a bunch of trial and error, and still not have anything work.

I'd still like to use Ubuntu because I like the interface, and because it is fast, but past a certain point I think it is fair to say Canonical is the problem, not the end users.

[rant][SIZE="1"][COLOR="Silver"]Let's see, Canonical is responsible for integrating the different programs used into one big package called the OS. They didn't write all the wireless Linux drivers themselves, but if those don't work: yes, let's blame them anyway.

Most hardware manufacturers spend plenty of time and money developing Windows and Mac OS drivers and not even bothering to acknowledge that someone might want to use their hardware on a Linux OS. I'm sure Canonical is also responsible for this in some way.

Some companies release their source code, even if they don't bother writing specific Linux drivers, allowing Linux users to see how they made their hardware work and write their own adaptations. Others refuse to do this, leaving the usage of at least some bits of proprietary software requirements for getting the devices to work. Naturally said pieces cannot be taken into the OS, as then it would not be open source anymore and thus they need to be left for the end user to install. Clearly this wouldn't be happening if Canonical was doing its job properly.[/COLOR][/SIZE][/rant]

If you hold such hatred towards Canonical, why not simply swap to some other Linux distribution? There are plenty of them around, where Canonical isn't screwing up everything and the interfaces and performance of Ubuntu are hardly unique.

Ever tried to install Mac OS or Windows on a bunch of computers that were originally running some other OS? Both worked out of the box every single time without having to download drivers or pull any tricks? Ever took a look at how many programs and drivers your typical Windows computer comes pre-installed with to ensure it works out of the box? Or the fact that Mac OS is only found natively on Macs which all run the same hardware and thus there aren't any unknown devices that need to be supported?

P.S. I'm not saying Canonical is perfect, far from it, but you could at least have the courtesy to blame it for the things it had a hand in.

---

### Post by neojames on 2009-11-08
> **greatn said:**
> At a certain point I don't think you have to blame yourself for being a noob, I think you have to blame Canonical. I plug in Windows Vista, it works, I have wireless. I plug in OS X, it works, I have wireless. I plug in Ubuntu 9.10, I need to go to terminal, type a bunch of stuff in I don't understand, download some files, do a bunch of trial and error, and still not have anything work.

I'd still like to use Ubuntu because I like the interface, and because it is fast, but past a certain point I think it is fair to say Canonical is the problem, not the end users.

On windows it works because it was created for windows, most of the devices I use work perfectly (except my wifi) which took hours to install on windows e.g my webcam. And with os x Apple make alot of the devises. Canonical and ubuntu may not be perfect but i've had alot more hours of unwanted cli time in windows to fix stuff like networking then i've had in ubuntu. Also most people will tell you to use terminal 'cause it is faster and less likely to go wrong than it would using a gui (I killed my wifi twice when I was trying to fix my wifi through a gui before I gave up and used cli)

---

### Post by greatn on 2009-11-08
Well the reason Ubuntu is the one I want to use is because it is the one that is supposed to be easy and user friendly. And to me it's always been great except for one thing. On Gutsy Gibbon my wireless would disconnect every 5 minutes and I'd have to unplug/replug my dongle. In 9.04 my microphone would not be recognized no matter what I tried.

What **really** frustrates me about 9.10 is that out of the box, 9.04 worked with my wireless. I downloaded the disc, clean installed it, and it worked with no problems(except the microphone isseus). 9.04 upgraded to 9.10 worked with my wireless straight away.  9.10 running off of the disc after I uninstalled because I wanted to do a clean install, worked straight away.

After I clean install 9.10 it doesn't work no matter how many hours I spend trying the various things I search for. I just get closer and it just gets more frustrating. So because this worked in every other version but not in this one, I don't blame the driver manufacture, I blame the OS. Because something that was compatible with my Dell 1525 with my 1395 PCI in all other versions and even on the same version's standalone disc was NOT present on the install! Now I'm to the point where I can see all of the surrounding networks but none of them will actually connect. And the various solutions listed in other threads have done nothing.

---

### Post by dungun on 2009-11-08
follow this...should work

[http://ubuntuforums.org/showpost.php?p=3996845&postcount=5](http://ubuntuforums.org/showpost.php?p=3996845&postcount=5)

---

### Post by brotherlen on 2009-11-08
Maybe you could try using wicd? I've had good luck with it and it's pretty intuitive.

---

### Post by greatn on 2009-11-08
And apologies for hijacking the thread, btw.

---

### Post by neojames on 2009-11-08
> **greatn said:**
> Well the reason Ubuntu is the one I want to use is because it is the one that is supposed to be easy and user friendly. And to me it's always been great except for one thing. On Gutsy Gibbon my wireless would disconnect every 5 minutes and I'd have to unplug/replug my dongle. In 9.04 my microphone would not be recognized no matter what I tried.

What **really** frustrates me about 9.10 is that out of the box, 9.04 worked with my wireless. I downloaded the disc, clean installed it, and it worked with no problems(except the microphone isseus). 9.04 upgraded to 9.10 worked with my wireless straight away.  9.10 running off of the disc after I uninstalled because I wanted to do a clean install, worked straight away.

After I clean install 9.10 it doesn't work no matter how many hours I spend trying the various things I search for. I just get closer and it just gets more frustrating. So because this worked in every other version but not in this one, I don't blame the driver manufacture, I blame the OS. Because something that was compatible with my Dell 1525 with my 1395 PCI in all other versions and even on the same version's standalone disc was NOT present on the install! Now I'm to the point where I can see all of the surrounding networks but none of them will actually connect. And the various solutions listed in other threads have done nothing.

I feel your pain but it isnt ubuntu excluseive, my old desktop virtually died when I put xp from 98 on it, but os's periodicly drop old drivers they are still there somewhere though. If it is a 3.5 mm jack it should work unless your sound card isnt compleatly recongnised.

---

### Post by goodlukeing on 2009-11-09
Wow, I didn't realise so many people would reply, I thought it was like yahoo answers where if you don't get a response initially there won't be much more. I don't know how to do that quote thing but i'll try,

> You can find which chip your wireless card is using and which driver is being associated with it by running **lshw -C network** from the terminal. Both can be important details for troubleshooting.I tried that, I don't know what all that info means but I'm guessing its the "product: PRO/Wireless 5100 AGN [Shiloh] Network Connection". What would I do now that I know what the driver is.

> Ok, how often do you face these phases and how long are they? Everytime I go to a new page it remains blank and says "loading" for about 30 seconds and then suddenly completely loads the page in my usual 5ish seconds or so.

> Maybe you could try using wicd?This is one of those things I've seen looking through stuff but didn't really get what it was or how to use it.

---

### Post by t0mppa on 2009-11-09
> **goodlukeing said:**
> I tried that, I don't know what all that info means but I'm guessing its the "product: PRO/Wireless 5100 AGN [Shiloh] Network Connection". What would I do now that I know what the driver is.

That is actually only the chip that your card uses. The driver is listed below that on the configuration line. What you can after knowing both them is search, if it's a known issue for said chip/driver and thus if there's a simple fix.

> **goodlukeing said:**
> > Maybe you could try using wicd? 
This is one of those things I've seen looking through stuff but didn't really get what it was or how to use it.

WICD is an alternative for Network Manager, a program to manage your network connections and yes, it has a GUI too, so not too hard to use. It sometimes works where Network Manager doesn't.

You can install it through Synaptic (System / Administration / Synaptic Package Manager) by typing *wicd* into the quick search field, then right clicking the wicd package once it shows up and choosing *Mark for Installation* and finally clicking the *Apply* button.

---

### Post by goodlukeing on 2009-11-10
Ahhhhh I see now, my driver is iwlagn. So where do I find a list of issues, or do I have to install some thing to make this driver work efficiently.

I tried WICD, looked pretty cool, but didn't fix my problem. Thanks for responding after my late replies.

---

### Post by t0mppa on 2009-11-10
There isn't a universal issue list with every possible wireless issue available, so the next best thing is just to ask your favorite search engine. If you can't find anything that sounds what you're experiencing, then it probably isn't a driver issue. I just don't know the Intel drivers well enough to be able to tell one way or the other.

One thing that comes in mind that could cause symptoms like yours would be slow DNS resolution, i.e., the service resolving which IP to contact when you ask the browser to go a certain domain like [www.google.com](www.google.com). You can test this by comparing the return time of pings (1) by domain name and pings by IP address (2). If the former are slow and the latter are quick, then you'll know that DNS resolution is causing at least some of your hickups.

(1) Just run **ping -c 10 <domain_name_or_ip_address>** from terminal for 10 pings, if you leave the count out, it will keep pinging until you interrupt it with Ctrl + C.
(2) You can find out IP addresses through **nslookup <domain_name>** or by pinging the domain for instance.

---

### Post by goodlukeing on 2009-11-12
I tried that lovely ping idea you had going, but unfortunately (well I guess its not a bad thing really, but it didn't help find the error) they timed out to be the same:

Total time for domain name: 9015ms
Total time for IP address: 9016ms

Well I guess there isn't much more to do, thanks for the help though, very much appreciated. I think I'll still stick to ubuntu anyway, still so many more benefits, for instance taking a normal amount of time to open "my computer". Maybe I could just use virtual box in the meantime to run windows and go on the internet.

---

