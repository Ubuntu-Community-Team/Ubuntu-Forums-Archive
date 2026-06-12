---
title: "MythTV on old Dell Dimension 4500S. What distro?"
date: 2010-01-20
forum: Multimedia Software
---

### Post by el_Paraguayo on 2010-01-20
My parents have an old Dell Dimension 4500S that's no longer being used and I also have a Hauppauge DVB Nova-T card that's sitting in a PC in a room with no aerial connection so I thought I might try to put the 2 together and have something that is slightly more useful than my VHS machine (hello 1980's!).
 
My question is really which distro I should be using.
 
 

It's clearly a fairly low-spec machine, but I'm not going to need it to do much:
[LIST]
[*]record 1 channel or playback recorded TV. (I won't be watching live TV on it and I won't be watching a recorded programme while recording another.)
[*]no internet connection
[*]don't need a desktop (unless MythTV needs one)
[*]no music
[/LIST]It seems to me I'm going to need just a bare-bones installation to keep memory usage to a minimum.
 
I may be new to Linux but I'm not intimidated by using command prompts (actually, I quite like the idea ;))
 
 
Any tips are greatly appreciated.
 
el_P

---

### Post by el_Paraguayo on 2010-02-08
Ok, a quick update:
 
Got my hands on the machine yesterday and had a go at getting MythTV up and running.
 
My distro of choice was [Mythbuntu 8.04 (alternate)]("http://cdimage.ubuntu.com/mythbuntu/releases/8.04/release/"). I'd read somewhere that 9.04 and onwards weren't running so well on Dimensions.
 
This installed pretty smoothly, no issues partitioning the disk or anything.
 
Problems started when I tried to set up the backend and I got the old "Cannot connect to database" message that seems fairly common.
 
I found the solution [here]("https://help.ubuntu.com/community/MythTV/Install/Troubleshooting#head-75ded5e7682340f0a88f9ed6ec69a68b6a8b4162"). I should have read the page in full instead of wasting a bit of time as the key bit was about reinstalling MySQL
```
sudo apt-get purge mysql-common
sudo apt-get install mythtv
```
 
The downside of this was that I lost the control panel that comes with Mythbuntu.
 
After that configuring MythTV was straightforward.
 
I then hooked it up to the aerial and TV and fired it up and it worked. Sort of.
 
I can display LiveTV but it tends to stutter a bit. Having checked out the specs I figured I could probably do with a bit more memory (I'm running 256MB at the moment) and so have ordered some more. Hopefully that should do it.
 
 

Outstanding points:
[LIST]
[*]I need to get the infra red sorted
[*]Get the machine to boot straight into frontend
[*]Bigger hard disk (if everything works)
[/LIST]

---

