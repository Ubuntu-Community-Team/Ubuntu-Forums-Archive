---
title: "Avoiding Gutsy, Waiting for Hardy"
date: 2007-12-13
forum: Multimedia &amp; Video
---

### Post by Bungo Pony on 2007-12-13
I haven't been around on this forum for a bit, and there's a good reason why. I haven't used Ubuntu in a while. In fact, my PC has been sitting in Windows for the past few weeks. Gutsy has been a major pain in the rear, and I still regret "upgrading" to it from Feisty. Here's my two major beefs with it:

1) I get a Gnome error most of the time Gutsy starts up. The error is just a pain and none of my icons appear on the desktop when this happens.

2) Gutsy Chooses a random sound card. I have my onboard sound, and a Creative sound card in my PC. The onboard sound is useful solely for the headphone jack on the front of the PC - I plug my FM Transmitter into it and listen to music upstairs. But I never know which sound card Gutsy will choose (it's usually the Creative card which I use for recording only as it works with Jack much better).

These two issues have really put me off doing ANYTHING with my Gutsy install. It's mostly just sitting there waiting for Hardy to be released and installed. My logic is why work on it when it will be outdated in six months with a stable release?

---

### Post by bruce89 on 2007-12-13
> **Bungo Pony said:**
> These two issues have really put me off doing ANYTHING with my Gutsy install. It's mostly just sitting there waiting for Hardy to be released and installed. My logic is why work on it when it will be outdated in six months with a stable release?

Gutsy is also a stable release, Hardy is just slightly more so.

> **Bungo Pony said:**
> In fact, my PC has been sitting in Windows for the past few weeks.

Why do people leave their computers on over the night? This is sheer lazyness.

---

### Post by ~LoKe on 2007-12-13
Issue 1 is probably easily resolved, but you've told us next to night.

Issue 2 happens to me as well, and was happening in Feisty just the same.  What makes you think Hardy will change this?

---

### Post by igknighted on 2007-12-13
> **Bungo Pony said:**
> I haven't been around on this forum for a bit, and there's a good reason why. I haven't used Ubuntu in a while. In fact, my PC has been sitting in Windows for the past few weeks. Gutsy has been a major pain in the rear, and I still regret "upgrading" to it from Feisty. Here's my two major beefs with it:

1) I get a Gnome error most of the time Gutsy starts up. The error is just a pain and none of my icons appear on the desktop when this happens.

2) Gutsy Chooses a random sound card. I have my onboard sound, and a Creative sound card in my PC. The onboard sound is useful solely for the headphone jack on the front of the PC - I plug my FM Transmitter into it and listen to music upstairs. But I never know which sound card Gutsy will choose (it's usually the Creative card which I use for recording only as it works with Jack much better).

These two issues have really put me off doing ANYTHING with my Gutsy install. It's mostly just sitting there waiting for Hardy to be released and installed. My logic is why work on it when it will be outdated in six months with a stable release?

Hardy wont be any more "stable" than Gutsy was/is necessarily.  It will just be supported longer.  When Dapper came out a couple years ago it was 2 months late and full of bugs... enough so that they re-released a new disk later that summer (hence 6.06.1).

You know that you can plug those front jacks in to the Creative card, then disable the onboard sound completely.  This would likely cure your sound woes.  The gnome error would probably go away with full updates.

EDIT: Wait, did you do a fresh install or an upgrade?  Upgrades almost always break stuff, try a fresh install.

---

### Post by eggdeng on 2007-12-13
> Gutsy Chooses a random sound card

Have you tried
```
sudo asoundconf list
```

to get the names of available cards. Then

```
sudo asoundconf set-default-card name_of_card
```

to set the default.

---

### Post by bruce89 on 2007-12-13
> **igknighted said:**
> Hardy wont be any more "stable" than Gutsy was/is necessarily.  It will just be supported longer.  When Dapper came out a couple years ago it was 2 months late and full of bugs... enough so that they re-released a new disk later that summer (hence 6.06.1).

I contest the fact it was "full of bugs". The 6.06.1 release was just like Debian's stable release updates such as 4.0r3. It's easier to install 6.06.1 than 6.06 then installing the huge number of updates.

6.06.2 should be out soonish.

---

### Post by FuturePilot on 2007-12-13
Yes, 6.06.1 was just a re-released image with all of the updates to that point. Like a service pack. Had nothing to do with it being too buggy. In fact if you look at the Hardy release schedule there's a planned date for 8.04.1

---

### Post by Bungo Pony on 2007-12-13
> sudo asoundconfig list

sudo: asoundconfig: command not found

> EDIT: Wait, did you do a fresh install or an upgrade?

I tried an upgrade first. When that really messed things up, I did a fresh install.

When I booted this round, I didn't get a gnome error. I'm hoping the last round of updates fixed it. I'll try the best two out of three and come back.

Maybe it's just me not looking forward to re-doing everything in 4 months. I've been looking forward to Hardy for quite some time, just for the sake of a 2 year supported release that will work on my machine.

---

### Post by ezphilosophy on 2007-12-13
> **bruce89 said:**
> 
Why do people leave their computers on over the night? This is sheer lazyness.

Downloads/Torrents?

---

### Post by Kingsley on 2007-12-13
> **ezphilosophy said:**
> Downloads/Torrents?
Or for bragging rights. I knew a guy that had an uptime of about 4 months on his Windows 2000 laptop.

---

### Post by Incense on 2007-12-13
Try Kubuntu gutsy. People seem to be pretty happy on that side of the fence. Even if you are not a KDE fan, it has to be better then windows right? ;)

Dapper was (IMO) the best ubuntu release, and I really hope they take their time to make the next LTS as good if not better. I still run dapper on one of my systems, and it has not let me down yet. We never did see the rumored 6.06.2 release though.

---

### Post by PatrickMay16 on 2007-12-13
I wish I hadn't updated my system from Feisty to Gutsy. Gutsy freezes regularly, plus there's a whole bunch of stupid glitches introduced (like the search function in nautilus, the volume control on the gnome panel, the position slider in totem, the gnome-power-manager dialogue, etc).
I'll wait for "hardy". If that sucks too, I'll install Debian.

> 
Dapper was (IMO) the best ubuntu release, and I really hope they take their time to make the next LTS as good if not better. I still run dapper on one of my systems, and it has not let me down yet. We never did see the rumored 6.06.2 release though

Yeah. Apart from the new theme, dapper was the all-around best of ubuntu. It was like the "ubuntu greatest hits" album.

---

### Post by eggdeng on 2007-12-14
> sudo: asoundconfig: command not found

Sorry, typo.
```
sudo asoundconf list
```

---

### Post by gn2 on 2007-12-14
Don't get your hopes up too much, I trialled Xubuntu 8.04Alpha1 and there doesn't seem to be any improvement at all over 7.10 which ran woefully slow on my laptop. 
Xubuntu 7.04 runs just fine though.

---

### Post by khurrum1990 on 2007-12-14
Has anyone tried Kubuntu 7.10, its awesome I had a lot of problems with Ubuntu as well. Since I used openSUSE 10.2 before I gave Kubuntu a try and it works well.

---

### Post by SunnyRabbiera on 2007-12-14
> **gn2 said:**
> Don't get your hopes up too much, I trialled Xubuntu 8.04Alpha1 and there doesn't seem to be any improvement at all over 7.10 which ran woefully slow on my laptop. 
Xubuntu 7.04 runs just fine though.

yes but its ALPHA, so its bound to be messy

---

### Post by olejorgen on 2007-12-14
> Why do people leave their computers on over the night? This is sheer lazyness.
Folding proteins [http://folding.stanford.edu](http://folding.stanford.edu)

---

### Post by gn2 on 2007-12-14
> **SunnyRabbiera said:**
> yes but its ALPHA, so its bound to be messy

Agreed, but it took over five hours to install from the Alternate CD, which is simply shocking compared with 7.04.

Irrespective of how buggy it is (or isn't), it just generally *feels* bloaty and slow.

---

### Post by graabein on 2007-12-14
> **bruce89 said:**
> Why do people leave their computers on over the night? This is sheer lazyness.

Server :confused:

---

### Post by t0p on 2007-12-14
> **Kingsley said:**
> Or for bragging rights. I knew a guy that had an uptime of about 4 months on his Windows 2000 laptop.

4 months on that POS?!!  Heck, I had problems keeping it up for 4 minutes!!

EDIT: "Keeping it up"?  hehe!

---

### Post by djsroknrol on 2007-12-14
My only beef with Gutsy is that VMware doesn't work with the 2.6.22-16 kernel for me...:(

---

### Post by Bungo Pony on 2007-12-14
I've had really good results with Windows 2000. What do you think is installed on my other partition? :)

My Linux usage has been mostly in DSL for the past little while, as I've been tweaking my garage PC again.

Just for the hell of it, I rebooted three times last night. The Gnome error seems to have disappeared, but on one of my restarts, X froze on me. Good old ctrl-alt-bksp.

There's so many great things about Ubuntu, but when it doesn't work, it's frustrating as hell.

---

### Post by Jimmey on 2007-12-14
> **gn2 said:**
> Don't get your hopes up too much, I trialled Xubuntu 8.04Alpha1 and there doesn't seem to be any improvement at all over 7.10.

It's not due for release until April '08. 

That around 4 and a half months of development time. When each release is only six months apart, then you'll notice that there's over two thirds of the time between the release of gutsy and the release of hardy left to go.

The Hardy you installed will be _nothing_ like the Hardy they will release. 

There have even been articles written about how drastically Ubuntu releases can be improved in a single month before their release.

It's like judging a cake by how the eggs smell. Crazy.

---

### Post by K.Mandla on 2007-12-14
I put this into Multimedia and Video in hopes that someone with a similar sound card arrangement will be able to help. 

Did you check for any bug reports about the issues you have with Gutsy?

And if Gutsy doesn't work for you, but Feisty does, why not reinstall Feisty? Is there something specific in Gutsy that you need?

---

### Post by khurrum1990 on 2007-12-14
> **djsroknrol said:**
> My only beef with Gutsy is that VMware doesn't work with the 2.6.22-16 kernel for me...:(
Hey how have u got the 2.6.22-16 kernel, I thought the latest was 2.6.22-14. I am using Kubuntu though so does that make a difference?

---

### Post by gn2 on 2007-12-14
> **Jimmey said:**
> It's not due for release until April '08. 

The Hardy you installed will be _nothing_ like the Hardy they will release. 


Let's hope so, because if it's anything like as bad as 7.10 on low-end hardware, those users will probably go elsewhere when 7.04 support expires.

---

### Post by Incense on 2007-12-14
> **gn2 said:**
> Let's hope so, because if it's anything like as bad as 7.10 on low-end hardware, those users will probably go elsewhere when 7.04 support expires.

Yeah, the system requirements say you need 256mb of ram to run the Live cd, but I found that not to be enough. I was unable to install it with the live disc on my 256 system, and installing from the alt CD brought about a system that was too slow to use. Dapper runs and installs without problems though. Don't quite know what happen to gutsy.

---

### Post by gn2 on 2007-12-15
> **Incense said:**
> Yeah, the system requirements say you need 256mb of ram to run the Live cd,

For 7.10 (and probably 8.04 as well) you need another 128mb RAM for the live CD, 384 is listed as the minimum on the 7.10 release notes.
I think the CPU minimum requirements should be re-assesed as well, it's dog slow on a PIII 500.

---

### Post by mjpolifka on 2007-12-15
As far as the sound cards, Fiesty did the same thing for me, though on my roommates computer it loaded the same one every time (just to piss me off I'm sure).  There is a How-To on here somewhere (I think in the wiki) telling you how to use alsa's configuration files to set the default soundcard.  it took me about an hour and worked great... until I upgraded and it deleted the custom config files...  Since then I've been too lazy to re-fix it, lol.

If you do a search for a how-to for multiple sound cards, you should find the answer you're looking for.  If not, let me know and I'm sure I'll be able to find it.

---

### Post by Bungo Pony on 2007-12-15
The error is back. So I took a screenshot of it

Also, when I was running Feisty, Opera (and almost any other program) would randomly freeze for a few seconds, and then keep running. It's worse in Gutsy.

Another question, how the heck can I switch between sound cards?

---

### Post by khurrum1990 on 2007-12-15
> **Bungo Pony said:**
> The error is back. So I took a screenshot of it

Also, when I was running Feisty, Opera (and almost any other program) would randomly freeze for a few seconds, and then keep running. It's worse in Gutsy.

Another question, how the heck can I switch between sound cards?
That is a known gutsy bug, I got that the first time I ran Ubuntu 7.10 RC1. I can't believe that bug stills exists. Some people get it, some people don't though. Thats why I switched to Kubuntu 7.10 and its awesome.

---

### Post by Bungo Pony on 2007-12-15
So, it just affects Gnome users?

I may end up switching to e17 if the bug remains for Hardy.

---

### Post by misfitpierce on 2007-12-15
I had a uptime of 1.4 months on ubuntu

---

### Post by khurrum1990 on 2007-12-15
Yeah its just for gnome users. KDE and XFCE users are safe.

---

### Post by khurrum1990 on 2007-12-15
oh yeah I forgot there r many sounds bugs in Ubuntu 7.10 due to gstreamer or something, again they don't exist for KDE and XFCE users either. Ubuntu really messed up its 7.10 release.

---

### Post by isaacj87 on 2007-12-15
I'm also holding back...

I tried a fresh install of Gutsy and it was such a bitter disappointment...I get that same sound error, my suspend and hibernate was broken (they were fine in Feisty) and an assortment of other annoyances. I'm sticking with Feisty for now, but I'm looking forward to Hardy. :)

---

### Post by djsroknrol on 2007-12-15
> **khurrum1990 said:**
> Hey how have u got the 2.6.22-16 kernel, I thought the latest was 2.6.22-14. I am using Kubuntu though so does that make a difference?

It's in Synaptic...but no kernel-headers, hence the problem with compiling for VMware :(

---

### Post by criskat777 on 2007-12-15
> **~LoKe said:**
> Issue 1 is probably easily resolved, but you've told us next to night.

Issue 2 happens to me as well, and was happening in Feisty just the same.  What makes you think Hardy will change this?

This use to happen to me as well and it was a very simple fix. Dang i wish i had bookmarked the page it was here on the threads some where. I have a Creative Live 5.1

---

### Post by khurrum1990 on 2007-12-15
I am using Kubuntu, but I couldn't find it, any idea whats wrong? Is it the standard kernel yet or not?

About the bugs, well this time it seems that most bugs r in Ubuntu 7.10, Kubuntu and Xubuntu 7.10 r perfectly fine. Kubuntu I know is ok cause I am using it, Xubuntu cause most people here seem to like it.

---

### Post by clonne4crw on 2007-12-15
Right now I'm using Feisty, upgraded from Edgy. Hearing all of this bad stuff about Gusty has scarred me into waiting. Then again, maybe I just won't upgrade again, period. I don't wanna mess up what I got. Spent hours getting it up and running.

---

### Post by khurrum1990 on 2007-12-15
> **clonne4crw said:**
> Right now I'm using Feisty, upgraded from Edgy. Hearing all of this bad stuff about Gusty has scarred me into waiting. Then again, maybe I just won't upgrade again, period. I don't wanna mess up what I got. Spent hours getting it up and running.
Yeah just wait for Ubuntu 8.04, even if it does have bugs since its an LTS release atleast u know they will get fixed. You could also install Kubuntu 7.10 though, its really stable.

---

### Post by reagentz on 2007-12-16
The only issue I've had with Gutsy was getting sound set right as well, default sound. I have onboard, a digital sound system that is detected through USB, and an Audigy card. Like you Gutsy would always set my USB sound as default. Of course, with USB sound system there's no Mic input, so Mic wouldn't work. I would set the Audigy CA0106 as Default through asound command and when I'd boot back up same thing. So I eventually pulled the USB, set the onboard sound to disable through BIOS and reinstall Gutsy with only the Audigy plugged in. After the reinstall it was set as my default. One at a time I hooked up the other sound devices and rebooted. I have everything hooked up now with no issues.

I never ran Feisty other than for 24 hours, the next morning Gutsy was released and I upgraded, and have ran it ever since. I like the distro, I've tried openSUSE, Gentoo, Fedora Core, Debian, Freespire, etc. I've really enjoyed Ubuntu the most. I'm also running it with GDE, and AWN with no issues, under the 64 bit version. Loading games like Quake Wars, Half Life 2, Guild Wars, Doom 3, Quake 4, Oblivion, World of Warcraft and Diablo 2 with no issues other than the normal tweaks to make them run under WINE, even updated to the latest WINE 0.9.51.

I can sympathize with you though man, I almost totally scrapped Ubuntu and went back to Last XP 16 just because of the sound problems. Don't let it get the best of you, uninstall evry piece of sound hardware physically from the PC but the one you want as default and reinstall it, I promise Ubuntu will make that the default and it will stay that way, then work around ALSA until you get the other hardware reinstalled and setup the way you want it. If you want some help or want to just chat about feel free to add me to your messengers, I won't have a ton of answers but I could help with getting in the right direction.

---

### Post by Tarmael on 2007-12-17
> **Kingsley said:**
> Or for bragging rights. I knew a guy that had an uptime of about 4 months on his Windows 2000 laptop.

I bet it was slow after a week.

---

