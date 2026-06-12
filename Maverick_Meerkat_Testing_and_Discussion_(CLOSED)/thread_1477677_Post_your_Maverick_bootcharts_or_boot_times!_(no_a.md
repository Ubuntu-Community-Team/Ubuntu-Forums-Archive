---
title: "Post your Maverick bootcharts or boot times! (no attachments please)"
date: 2010-05-09
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Starks on 2010-05-09
The purpose of this thread is to serve as an informative measuring stick for any and all boot improvements over Lucid during the Maverick development cycle.

In order to participate, just install bootchart  through apt-get, aptitude, synaptic or however you like. The  bootchart PNG will be created in the /var/log/bootchart/ directory.

I kindly ask that all participants refrain from posting their bootcharts as attachments. Image attachments are worthless on this site because the images are resized to an unreadable and wholly non-useful degree. All images are to be hosted remotely on sites like Imageshack, Imgur, Photobucket, and Bayimg to name a few.

**TO REITERATE: ATTACHMENTS ARE NOT PERMITTED AND WILL NOT DISPLAY A READABLE IMAGE.**

Because bootcharts can be over 1MB in size and large in resolution, regular direct image links are preferred over direct images links wrapped in [img] tags or added via the "Insert Image" button. Thumbnail images are fine.

Finally, do be mindful of the fickle nature of bootchart. The PNG file may take a minute or two to be generated along with the TGZ file after the boot finishes. Reprofilings of ureadahead can cause wild improvements or regressions of your boot time.

---

### Post by Starks on 2010-05-09
And to start things off...

[http://img269.imageshack.us/img269/3630/kingfishermaverick20100.png](http://img269.imageshack.us/img269/3630/kingfishermaverick20100.png)

My best Lucid boot time ever was roughly 20 seconds. The above image is pretty close (Karmic and Lucid alpha average was 40 seconds) and should be a pretty fair assessment of what Alpha 1 will probably feature.

Kernel: 2.6.34 (latest RC)
Drivers: X Server 1.8.1, Mesa 7.9, Gallium 0.4, Intel 2.11
Hardware: 1.6GHz Core Duo T2050, 2GB DDR2, 160GB 5400rpm SATA, Intel 945GM

---

### Post by plun on 2010-05-09
My bootcharts are broken because I am using 2.6.34 kernels, no idea howto fix it either, anyone with a good tip  ?

---

### Post by philinux on 2010-05-09
I always post a crop/screenshot of the png anyway, which is readable.

---

### Post by plun on 2010-05-09
It works sometimes after a check....

Still no idea howto control bootcharts.](*,)

What is plymouthd and ureadahead doing ?


[[img]http://ubuntu-pics.de/thumb/59844/plun_laptop_maverick_20100507_1_xHj4Lr.png[/img]](http://ubuntu-pics.de/bild/59844/plun_laptop_maverick_20100507_1_xHj4Lr.png)

---

### Post by plun on 2010-05-09
wrong quote....  24 seconds anyway...

---

### Post by ranch hand on 2010-05-14
Well, I am impressed.  Plymouth is by no means fixed for my box but by the very Gods the devs have done some amazing things.

I am still running with no splash in my menu entry.

I do have to login.

I just installed the .34 kernel and installed ureadahead.

Ureadahead was removed so that I could boot without having to use recovery mode under the .32 kernel.

This is an upgrade OS 9.04>9.10>10.04>10.10.

I just restarted 3 times to get the kernel and ureadahead up to speed.

By bootchart 44.74 seconds.  This may not impress some but it is a good 20 to 30 seconds off my very best times under .32.

---

### Post by Neezer on 2010-05-14
> **plun said:**
> It works sometimes after a check....

Still no idea howto control bootcharts.](*,)

What is plymouthd and ureadahead doing ?


[[img]http://ubuntu-pics.de/thumb/59844/plun_laptop_maverick_20100507_1_xHj4Lr.png[/img]](http://ubuntu-pics.de/bild/59844/plun_laptop_maverick_20100507_1_xHj4Lr.png)

How do you get that boot chart created? or where is it located after you boot?

---

### Post by ranch hand on 2010-05-14
You need to install "bootchart".

It is located at /var/log/bootchart.

If you have bootchart installed already and do not get the graphic file a bug on it.  Or better join one.  It seems to be buggy in some instances that make no sense to me at all.

---

### Post by Owen.C93 on 2010-05-14
Can I add that it may be better to enable automatic login. Because on my machine it included the time for me to login.

It might be worth including ways to improve boot speeds in the OP if you feel like it :)

---

### Post by ranch hand on 2010-05-14
Yes auto login is faster (about 2 seconds on this box) and it should be remembered that the 10sedond target in including auto login.

I do not use auto login except for the first boot after the install of ISO-testing OS'.  If I wanted that sort of lax security I would use some MS crap.

---

### Post by Starks on 2010-05-22
[[IMG]http://img532.imageshack.us/img532/3630/kingfishermaverick20100.th.png[/IMG]]("http://img532.imageshack.us/img532/3630/kingfishermaverick20100.png")

---

### Post by vigstrom on 2010-05-23
Fresh system, ie, new install of Lucid 64bit, then upgraded.
Couldn't get bootchart to produce a png until i changed:
```
return "RSDTZXW".index(flag) + 1 

```in 
/usr/lib/pymodules/python2.6/pybootchartgui/draw.py
to
```
return "RSDTZXW".find(flag) + 1

```
more info here: 
[https://bugs.launchpad.net/ubuntu/+source/pybootchartgui/+bug/512172](https://bugs.launchpad.net/ubuntu/+source/pybootchartgui/+bug/512172)

[http://farm5.static.flickr.com/4035/4632385236_a6b2fb7cae_o.png](http://farm5.static.flickr.com/4035/4632385236_a6b2fb7cae_o.png)

---

### Post by ranch hand on 2010-05-23
The line referenced above is at about line 105.

---

### Post by cimh on 2010-05-26
Does anyone know if trying to reach the 10s boot on an ssd netbook is still an aim of maverick - I have not seen it talked about too much?

Lucid did a superb job of reducing the boot time but did not achieve its target, at least not according to most people. I still take my hat off to the team for their great achievements. 

With my eeepc 901 (ssd) I was getting on average 24s from switch on to desktop (take away 6s for grub that makes 18 for lucid). My guess is that to bring this down a lot more a different or a streamlined dm would have to be used?

cimh
eee901 ubuntu,lubuntu,puppeee

---

### Post by Starks on 2010-05-26
10 seconds from grub is still a pipedream.

---

### Post by kansasnoob on 2010-05-26
Why "no attachments"?

---

### Post by taavikko on 2010-05-26
> **kansasnoob said:**
> Why "no attachments"?

Cause they do not show correctly...

---

### Post by cariboo on 2010-05-26
> **kansasnoob said:**
> Why "no attachments"?

Due to database problems, we had to limit the size of jpg/png attachments. I use [http://imgur.com/](http://imgur.com/) for uploading images

---

### Post by cecilpierce on 2010-05-26
didnt work for me!

---

### Post by ranch hand on 2010-05-26
Can't read that.

---

### Post by cecilpierce on 2010-05-26
> **ranch hand said:**
> Can't read that.

I know, Ive tried before and same thing, I just dont know how do do the dag-nab thing ! I give up....

anyhow it was 44.45 secs

---

### Post by cecilpierce on 2010-05-26
[http://yfrog.com/jdcecildesktopmaverick201p](http://yfrog.com/jdcecildesktopmaverick201p)

see if imageshack worked ?

---

### Post by ranch hand on 2010-05-26
Works just fine.

---

### Post by cariboo on 2010-05-26
It's easy see:

[http://imgur.com/pEz6t](http://imgur.com/pEz6t)

Bootchart

[[IMG]http://imgur.com/pEz6tl.jpg[/IMG]](http://imgur.com/pEz6t.png)

---

### Post by cecilpierce on 2010-05-26
Yea easy to say ! If I can just remember how I did it ?
I don't know how to read the chart but it sure has alot of blue at the end, whats taking so long to boot ?
My Lucid takes over a minute and the other Maverick on here takes 37 secs.

---

### Post by kansasnoob on 2010-05-27
> **taavikko said:**
> Cause they do not show correctly...

I was thinking along the lines of attaching as a tar.gz rather than a screenshot.

That's what I'd done during Lucid testing.

I guess some people don't like opening attachments like that though.

---

### Post by ranch hand on 2010-05-27
> **kansasnoob said:**
> I was thinking along the lines of attaching as a tar.gz rather than a screenshot.

That's what I'd done during Lucid testing.

I guess some people don't like opening attachments like that though.
I did that myself and think it is a much better plan.

Of coarse you do have to do a few more clicks to view it but you can have more than one image too, showing a series of results or results from more than one OS.

---

### Post by ronacc on 2010-05-27
20.6 sec here , automatic delay set to 3 sec but it is taking longer for some reason .

---

### Post by cimh on 2010-05-27
Following up on my question of whether a 10s boot on a netbook is still a goal for maverick.

I think the answer is no, at least not for the std version.

According to Marks blog
[http://www.markshuttleworth.com/archives/383](http://www.markshuttleworth.com/archives/383)

I think this goal has now been transplanted into the netbook edition sporting unity.

I'm playing with this at the moment and first impressions are that its neater than previous netbook remix's tho its no faster than std lucid just now.

cimh
eee 901

---

### Post by ktp on 2010-05-27
> **Starks said:**
> 10 seconds from grub is still a pipedream.

maybe not 10 seconds but close for me...~15 seconds...and that's with regular old SATA harddrive.  

I have to say, if you have not done clean install of 10.04...you should try it.  I was getting lot longer boot time when I upgraded to 10.04.  But after clean install, with ext4, first thing I notice is the boot and shutdown time improvements.  I get little better boot time without bootchart also...maybe one or two seconds.

---

### Post by ronacc on 2010-05-28
my bootchat times always seem to be pleasingly short at the start of a dev cyle and then double or even tripple during the cycle .not because of my adding starup apps , I install most of those the first day or 2 and usually do several complete reinstalls ( / and home) during the cycle .

---

### Post by davideotape on 2010-05-29
> **vigstrom said:**
> Fresh system, ie, new install of Lucid 64bit, then upgraded.
Couldn't get bootchart to produce a png until i changed:
```
return "RSDTZXW".index(flag) + 1 

```in 
/usr/lib/pymodules/python2.6/pybootchartgui/draw.py
to
```
return "RSDTZXW".find(flag) + 1

```
more info here: 
[https://bugs.launchpad.net/ubuntu/+source/pybootchartgui/+bug/512172](https://bugs.launchpad.net/ubuntu/+source/pybootchartgui/+bug/512172)


I'm not getting a .png either, but I'm not getting the crash described in that bug report. Should I open a new report?

---

### Post by MacUntu on 2010-05-29
Do you have both packages - bootchart and pybootchartgui - installed?

---

### Post by davideotape on 2010-05-30
```
$ sudo apt-get install bootchart pybootchartgui
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bootchart is already the newest version.
pybootchartgui is already the newest version.
pybootchartgui set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

```

Actually, I have got one .png for my most recent boot.

---

### Post by ranch hand on 2010-06-14
As has been mentioned several times, the speed seems to go down as development continues on these test OS'.

I think I may have a record though.  This is on an install upgraded from 10.04 which was installed using the RC for 10.04 in ISO testing.

It has always been one of my fast booting installs, under 30 seconds a couple of times.

The last time boot chart worked on that install was the 11th (I think it quit from shock)

Boot time was 3:10:53.

---

### Post by cariboo on 2010-06-14
His system is still booting in under 20 seconds.

[[IMG]http://imgur.com/AAZnIs.jpg[/IMG]](http://imgur.com/AAZnI.png)

The one thing I have found it that my netbook seems to take longer to come out of hibernation, than it does to reboot. I haven't installed bootchart on it yet.

---

### Post by plun on 2010-06-14
14.73.... I3 Laptop with SSD disk

[[img]http://ubuntu-pics.de/thumb/83447/plun_laptop_maverick_20100613_5_1O6AG2.png[/img]](http://ubuntu-pics.de/bild/83447/plun_laptop_maverick_20100613_5_1O6AG2.png)

---

### Post by ranch hand on 2010-06-14
My son is on 10.04 and he is booting in the 15 second range all the time.  Loves it.

My main installation is doing about the same as always, so far, two boots today 1:13:90 and 1:05:36.

Clean installs do better, one installed from the 10.10-A1 ISO-RC did 32:46 yesterday.

---

### Post by Starks on 2010-07-17
[http://img188.imageshack.us/img188/3630/kingfishermaverick20100.png](http://img188.imageshack.us/img188/3630/kingfishermaverick20100.png)

I like what I see.

---

### Post by TDK800 on 2010-07-17
Maverick alpha-2:
[http://img693.imageshack.us/img693/9596/xmaverick201007171.png](http://img693.imageshack.us/img693/9596/xmaverick201007171.png)

any suggestions for speeding it up?

---

### Post by 23dornot23d on 2010-07-18
This is booting from a 500 Gig Seagate USB drive so may explain the speed ..


[Bootchart]("http://img594.imageshack.us/img594/4287/keithlaptopmaverick2010.png").

This was a clean install today on sdc11 my no 2 USB drive ......  **26 secs**

(** Impressive is 3 times faster than my previous bootchart on this same drive** )

From the Daily build CD ......

---

### Post by Starks on 2010-07-18
I find it confusing that my 4 year old, low end laptop is outbooting brand new, mid range and top of the line systems.

---

### Post by 23dornot23d on 2010-07-18
I think its the transfer speeds on USB drives .... if I do a test on the main drive it should boot a lot quicker .... 
might try it later on .... but its fast enough for me at the moment.

I will add another one later on ....

[Bootchart Ultimate Edition of Maverick]("http://img829.imageshack.us/img829/4287/keithlaptopmaverick2010.png")

For some reason they run a virus check too .... this is double the clean install of Maverick and runs
from my main drive sda10 **46 secs**

---

### Post by Starks on 2010-07-21
Clean install with my replacement hard drive.

[http://img210.imageshack.us/img210/3630/kingfishermaverick20100.png](http://img210.imageshack.us/img210/3630/kingfishermaverick20100.png)

New record for me.

---

### Post by ranch hand on 2010-07-21
Lucky bugger.  That is really nice.

---

### Post by cecilpierce on 2010-07-21
> **Starks said:**
> Clean install with my replacement hard drive.

[http://img210.imageshack.us/img210/3630/kingfishermaverick20100.png](http://img210.imageshack.us/img210/3630/kingfishermaverick20100.png)

New record for me.

WOW! best time for me 37s, have you tried the 2.6.35-9 ?

---

### Post by ktp on 2010-07-21
> **Starks said:**
> Clean install with my replacement hard drive.

[http://img210.imageshack.us/img210/3630/kingfishermaverick20100.png](http://img210.imageshack.us/img210/3630/kingfishermaverick20100.png)

New record for me.

since lucid, I am also getting around ~17 seconds (did clean install with ext4).

---

### Post by jerrylamos on 2010-07-25
40 seconds one time, 33 another.

Do note boot was from IDE drive with 8 partitions, booting from an extended partition #8.

Do note Grub thinks the IDE is drive b and the sata drive a, while maverick install thinks the IDE is drive a and the sata drive b.  Messes up Alpha 2 install since after install Grub is looking for a UUID on one drive and it is actually on the other, and Grub is entirely too dumb to look around and can't even post its initial menu.  Yes, there's a launchpad bug.  I don't expect any fix.  Alpha 1 was O.K.

3.33 ghz Celeron.

Jerry

---

### Post by cariboo on 2010-07-26
A little bit slower than Lucid

[[IMG]http://imgur.com/pD29Kl.jpg[/IMG]](http://imgur.com/pD29K.png)

---

### Post by Starks on 2010-08-09
I think pybootchartgui is broken again.

[https://bugs.launchpad.net/ubuntu/+source/pybootchartgui/+bug/615308](https://bugs.launchpad.net/ubuntu/+source/pybootchartgui/+bug/615308)

---

### Post by cariboo on 2010-08-09
> **Starks said:**
> I think pybootchartgui is broken again.

[https://bugs.launchpad.net/ubuntu/+source/pybootchartgui/+bug/615308](https://bugs.launchpad.net/ubuntu/+source/pybootchartgui/+bug/615308)

It still works for me, todays bootchart after updates:

[[IMG]http://imgur.com/kMgYLs.jpg[/IMG]](http://imgur.com/kMgYL.png)

---

### Post by MacUntu on 2010-08-09
> **Starks said:**
> I think pybootchartgui is broken again.

[https://bugs.launchpad.net/ubuntu/+source/pybootchartgui/+bug/615308](https://bugs.launchpad.net/ubuntu/+source/pybootchartgui/+bug/615308)

"IOError: error while writing to output stream"

You're trying to write a file to '/var/log/bootchart', so better start bootchart with 'sudo'. ;)

---

### Post by Starks on 2010-08-09
I know, but it doesn't generate the PNG on boot either.

---

### Post by MacUntu on 2010-08-09
Hm, did you modify your '/etc/init/bootchart.conf'? [[http://paste.ubuntu.com/]](http://paste.ubuntu.com/]) Maybe added 'bootchart=disable' to your grub kernel line?

---

### Post by vc_ubu on 2010-08-23
Was playing with bootchart yesterday after upgrading to Maverick Alpha 3 (from a Lucid) and found this thread...

Managed to get **10.35 seconds** out of my rig :D it's a i7-920 (not OC'd) with triple-channel DDR3 memory @ 1600mhz and a SSD (OCZ Vertex)... which is a slightly obscene rig for running Ubuntu but I also use it for video editing and the like w/ Windows.

So 10 seconds seems vaguely possible, but only on top-shelf hardware and SSDs.

Interestingly, I did a few other runs trying to break the 10sec barrier, and sometimes I get higher throughput on the disk, but whenever that happens it also takes longer to boot (~14sec). Odd. 

click to enlarge
[[IMG]http://imgur.com/qp6qAl.jpg[/IMG]]("http://imgur.com/qp6qA.jpg")

---

### Post by Mills00013 on 2010-08-24
I dont really know what I'm looking at but here is mine from my 2.5Ghz 4,1 Macbook Pro. I also have a Samsung PM800 256Gb SSD. This is without any optimization, just installed and restarted.

[IMG]http://imgur.com/Imv1Q.png[/IMG]

---

### Post by ranch hand on 2010-09-08
Well, I had a shock today.

Got the libplymouth2 and plymouth upgrades this morning on my through away OS' and they seemed to work pretty well there but no real difference.

Decided to chroot upgrade this, my main testing OS, to see the effect here.  I have been able to boot in under 50 seconds for some time now, around 47 usually.

First boot today, right after the upgrade, was 42.43.   This is definitely a record low time.  45.8 is the best I have ever done before.

---

### Post by Starks on 2010-09-08
I think my bootchart is on the fritz. Certainly doesn't feel like 90 seconds.

[http://img836.imageshack.us/img836/1042/ericlaptopmaverick20100.png](http://img836.imageshack.us/img836/1042/ericlaptopmaverick20100.png)

---

### Post by 23dornot23d on 2010-09-08
I am worried ..... am having lots of problems at the moment ..... and 1:30 to boot is not what I have been used to.


[COLOR=Red]CAN ANYBODY TELL ME IF THE EXE should be here in this chart ..... I have a feeling its a virus or its something else - but I have never noticed it there before  .....

I am running BURG at the moment as a bootloader ..... could it be to do with that ?



[/COLOR][http://img80.imageshack.us/img80/3508/ubuntumaverick201009081.png](http://img80.imageshack.us/img80/3508/ubuntumaverick201009081.png)[COLOR=Red] 



More to the point if it is - how do I stop it ..... and track where it is being run from .......
[/COLOR]

---

### Post by ronacc on 2010-09-08
fresh install at beta onto an ssd , 6 to 7 seconds grub to login and another couple login to desktop.

---

### Post by MacUntu on 2010-09-08
And how long from pushing the button till GRUB? :P

**DIE, BIOS, DIE!**

---

### Post by ronacc on 2010-09-08
actually the bios does have some use , I use it to select which drive is the first boot drive .I have multiple drives and multiple installs and multiple grubs .

---

### Post by 23dornot23d on 2010-09-08
Great boot time Ronacc - do you have a chart to post .... ?

Mine is better now I have got rid of the Windows Partition .... and the EXE that was running .....
I sussed it out ,,,,,, was running the System Restore in System32 ......  obviously was a Windows Virus
that had managed to get on there ,,,,,, its gone now though .........

Here is a better boot chart for mine now ,,,,, and things are running a lot better too ..... hopefully some of my issues
with the system will have gone too ...... ( like 2 users showing up ..... I need to be more careful now )

I would advise others to do a bootchart too ..... I might not have noticed the EXE that was running first otherwise .....

39 seconds for mine now and the new Install worked great too ..........

[http://img820.imageshack.us/img820/4287/keithlaptopmaverick2010.png](http://img820.imageshack.us/img820/4287/keithlaptopmaverick2010.png)

---

### Post by Starks on 2010-09-08
Umm, exe is not a virus. You wiped your partition for no reason.

---

### Post by 23dornot23d on 2010-09-08
Oh cheers ...... 

It seemed to be causing a long delay and its not there on the new bootchart !!!! since I did it ....

I only removed the Window partition ......... which I never use nowadays anyhow.

What is the Exe then ?

What did  it do on the previous chart to the last one I posted ? [B][COLOR=Red]

( That took 17 seconds to run before anything else started up )

[COLOR=Black]Cannot find EXE on the new chart anywhere ..... sounds like an abbreviation for Executable ..... just a guess 


Got it ...... its the bootable USB ,,,,,, will check later on ......... thanks for the quick response .....
[/COLOR] [/COLOR][/B]

---

### Post by ranch hand on 2010-09-08
Any reason is a good reason to delete MS.

---

### Post by 23dornot23d on 2010-09-08
I think I have been looking for a reason to wipe it completely ..... ):P

That one was as good a reason as I needed ;)

It also gave me a full 60 Gig back ..... for another install of my favourite System LINUX

---

### Post by ktp on 2010-09-08
> **ronacc said:**
> fresh install at beta onto an ssd , 6 to 7 seconds grub to login and another couple login to desktop.

nice...time to go buy ssd.  I wonder how fast i can get mine, which is ~14 seconds to desktop.

---

### Post by Starks on 2010-09-19
[http://img840.imageshack.us/img840/3630/kingfishermaverick20100.png](http://img840.imageshack.us/img840/3630/kingfishermaverick20100.png)

22 seconds.

---

### Post by karmila on 2010-09-20
Here is mine [http://imgur.com/NZA2j.png](http://imgur.com/NZA2j.png)

24.39 s on 80GB ATA MAXTOR STM380215AS.

---

### Post by VinDSL on 2010-09-20
Whoa!  That's creepy!

Makes me *feel* like a computer voyeur, or something...  :-k

[[COLOR="Red"]http://vindsl.com/images/Zuul-maverick-20100920-1.png[/COLOR]]("http://vindsl.com/images/Zuul-maverick-20100920-1.png") (26.45 sec)

Old Skool:  DFI LanParty with an Intel P4 Extreme Edition CPU

---

### Post by VinDSL on 2010-09-20
Well, well...  Isn't that interesting?!?!?

As fate would have it, there was a kernel update, a few minutes ago, and it shaved 5.3 seconds off my boot time, e.g. 20% quicker now!  :D

[[COLOR="Red"]http://vindsl.com/images/Zuul-maverick-20100920-2.png[/COLOR]]("http://vindsl.com/images/Zuul-maverick-20100920-2.png") (21.16 sec)

---

### Post by cecilpierce on 2010-09-20
mine went from 50.85 to 48.20 on this install but one other beta install jumps up and down drastic from over one minute down to 36 seconds. :confused:

---

### Post by skeetre on 2010-10-02
Here's mine...
[http://skeetre.com/bootchart/meerkat-quad-maverick-20101002-3.png]("http://skeetre.com/bootchart/meerkat-quad-maverick-20101002-3.png")
10.06 seconds.

---

### Post by sylvester_0 on 2010-10-03
4.7 seconds using RC freshly installed to 40G Intel X-25M :)
[http://i.imgur.com/buo0G.png](http://i.imgur.com/buo0G.png)

---

### Post by skeetre on 2010-10-03
> **sylvester_0 said:**
> 4.7 seconds using RC freshly installed to 40G Intel X-25M :)
[http://i.imgur.com/buo0G.png](http://i.imgur.com/buo0G.png)

That's amazing! 4.7 seconds...

I might have to try a fresh install and disconnect my other drives, see what I can do to speed it up.

But then again, I rarely reboot. I'm kind of surprised at all the attention towards boot times when the normal user environment is what needs to be sped up.

---

### Post by ricsi-pontaz on 2010-10-03
Here's mine:

[http://imgur.com/Mmfma.png](http://imgur.com/Mmfma.png)

23.61

---

### Post by ktp on 2010-10-03
> **sylvester_0 said:**
> 4.7 seconds using RC freshly installed to 40G Intel X-25M :)
[http://i.imgur.com/buo0G.png](http://i.imgur.com/buo0G.png)

sweet!!!  I am going to have to do fresh install sometime after it's release.

---

### Post by VinDSL on 2010-10-03
> **skeetre said:**
> That's amazing! 4.7 seconds...4.8 sec actually, but true enough!  

And, we're talking about a $99 SSD -- which is even more amazing...


> **skeetre said:**
> But then again, I rarely reboot. I'm kind of surprised at all the attention towards boot times when the normal user environment is what needs to be sped up.It's *mostly* bragging rights, I suppose.

But then again, I live in a scorchingly hot environment.  I spend a small fortune refrigerating the air in my house ($300/mo), just to make it liveable.  All of these computers, I'm running, act like space heaters.  It's them vs. my air conditioning system.  Thus, I turn them off, when I go to bed.

Sooo, fast boot times have a practical component, in my experience...

---

### Post by tanari on 2010-10-04
34.16

[http://imgur.com/YFREW.png](http://imgur.com/YFREW.png)

---

### Post by sendblink23 on 2010-10-04
I'd expected mine to be faster but I feel it stinks for my hardware

[http://img808.imageshack.us/img808/7343/sendblink23ms7577maveri.png](http://img808.imageshack.us/img808/7343/sendblink23ms7577maveri.png)
time: 25.91

I definitely need to switch over to SSD's, these 7200rpm HD's are slow nowadays

---

### Post by MacUntu on 2010-10-04
> **sendblink23 said:**
> [http://img808.imageshack.us/img808/7343/sendblink23ms7577maveri.png](http://img808.imageshack.us/img808/7343/sendblink23ms7577maveri.png)
time: 25.91
IMO there's too much I/O going on after the ureadahead process finished.

Delete the pack file in '/var/lib/ureadahead' and reboot. Wait a minute or two after the desktop is loaded and then reboot again to get a new chart. That definitely should shave off some seconds.

---

### Post by philinux on 2010-10-04
First reboot with bootchart
[http://imagebin.ca/view/fnS666.html](http://imagebin.ca/view/fnS666.html)

21.94 sec.

Then after a further reboot.

[http://imagebin.org/116954](http://imagebin.org/116954)
17.92

---

### Post by sendblink23 on 2010-10-04
> **MacUntu said:**
> IMO there's too much I/O going on after the ureadahead process finished.

Delete the pack file in '/var/lib/ureadahead' and reboot. Wait a minute or two after the desktop is loaded and then reboot again to get a new chart. That definitely should shave off some seconds.

I think you crippled something on my system because now I always get upon startup(right before Ubuntu 4 dots) an error of that ureadahead

and now ITS MUCH SLOWER my boot.. thanks allot... I did the user-error of not making a backup of that folder before erasing it

I rebooted about 6 times its pretty much on all been the same slow & I'm still getting the startup error I mentioned

Time: 39.93
[http://img695.imageshack.us/img695/7343/sendblink23ms7577maveri.png](http://img695.imageshack.us/img695/7343/sendblink23ms7577maveri.png)

Any way of reinstalling ureadahead ?

---

### Post by Starks on 2010-10-04
Clearing that folder shouldn't do that.

Just apt-get remove and then apt-get install. aptitude reinstall usually isn't good enough.

---

### Post by MacUntu on 2010-10-04
> **sendblink23 said:**
> that folder before erasing it

You didn't delete the whole folder, did you? Just the pack file in it!

Anyways, to reinstall ureadahead do:

```
sudo apt-get purge ureadahead
sudo apt-get install ubuntu-minimal
```

First one will remove ureadahead (and the meta-package ubuntu-minimal), second one will reinstall both.

---

### Post by sendblink23 on 2010-10-04
> **MacUntu said:**
> You didn't delete the whole folder, did you? Just the pack file in it!

Anyways, to reinstall ureadahead do:

```
sudo apt-get purge ureadahead
sudo apt-get install ubuntu-minimal
```

First one will remove ureadahead (and the meta-package ubuntu-minimal), second one will reinstall both.

hehehe when I read the word pack(somehow I ignored the word "file" next to it lol) I assumed you meant the whole pack of that folder :P

Going to reinstall it with your commands ;)

-----
update

Yup it fixed it - ureadahead

I think the slow booting now is not related to it because I still am in the 39 seconds now... I think it has to do with the updates, its the only changes I've done since my earlier post
[http://img180.imageshack.us/img180/7343/sendblink23ms7577maveri.png](http://img180.imageshack.us/img180/7343/sendblink23ms7577maveri.png)

---

### Post by sendblink23 on 2010-10-04
I rebooted again after the last post...
And it did shed seconds... faster than my 1st post

Time: 19.13
[http://img826.imageshack.us/img826/7343/sendblink23ms7577maveri.png](http://img826.imageshack.us/img826/7343/sendblink23ms7577maveri.png)

---

### Post by M4570D0N on 2010-10-08
I'm hoping someone might be able to provide some insight here. 1st, is there a thread here or some good resources elsewhere on how to decrease boot times? My boot time seems to be getting worse lately. I did a fresh install to the 10.10 RC  and the boot time was a little bit slower than it was Mint 9 gnome, but it was ok I suppose. I started out arond 24-25 sec, but now I am consistently averaging over 30 seconds, and the time from when I type in my login password, to when it shows my desktop is also noticeably longer as well. When I was on Mint 9, I was averaging 15-18 sec. boot times. Can anyone help me figure out what's causing the extended boot time?

Oct. 8th (32.77 sec.):
[http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/aaron-HP-Pavilion-dv5-Notebook-PC-maverick-20101008-2.png](http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/aaron-HP-Pavilion-dv5-Notebook-PC-maverick-20101008-2.png)

Sept. 30th (25.45 sec.):
[http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/aaron-HP-Pavilion-dv5-Notebook-PC-maverick-20100930-2.png](http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/aaron-HP-Pavilion-dv5-Notebook-PC-maverick-20100930-2.png)

Sept 5th on Mint 9 gnome (15.45 sec.):
[http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/aaron-laptop-isadora-20100905-1.png](http://i596.photobucket.com/albums/tt45/SH00TTH3H0STAG3/aaron-laptop-isadora-20100905-1.png)

---

### Post by solitaire on 2010-10-09
Woo!!!
20.9 second boot!!

[http://i12.photobucket.com/albums/a233/s0litaire/europa-maverick-20101009-2.png](http://i12.photobucket.com/albums/a233/s0litaire/europa-maverick-20101009-2.png)

wonder if i can tweak it any more?... ~_~

Anyone know what the vertical dashed lines on the chart mark?

---

