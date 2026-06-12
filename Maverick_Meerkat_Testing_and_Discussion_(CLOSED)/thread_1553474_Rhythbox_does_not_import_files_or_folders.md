---
title: "Rhythbox does not import files or folders"
date: 2010-08-15
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Stoneface on 2010-08-15
Just tried to add a folder with mp3s and wmas to Rythmbox, but it does not import anything at all. I installed all restricted codex as far as I can see so that should not be an issue. Did find one error:
```
[30330.926960] rhythmbox[16015]: segfault at 34 ip 03443771 sp b33e3cf8 error 4 in libc-2.12.so[333a000+157000]
```
Could someone tell me what else I should check?

NB Doing this on my Maverick Meerkat development box

---

### Post by Elfy on 2010-08-15
moved to meerkat forum - please post meerkat threads in that forum.

[http://ubuntuforums.org/forumdisplay.php?f=385](http://ubuntuforums.org/forumdisplay.php?f=385)

---

### Post by Stoneface on 2010-08-15
@ Forestpiskie Thanks. Will do. Just tried to import again into Rythmbox. No folder with mp3s nor wams was imported.

---

### Post by Stoneface on 2010-08-15
Made a bug report [https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/618207](https://bugs.launchpad.net/ubuntu/+source/rhythmbox/+bug/618207) and just tried to import the files/folders into Rhythmbox on stable Lucid Lynx. this went smoothly. So definitely a Maverick Meerkat problem.

---

### Post by mc4man on 2010-08-15
> So definitely a Maverick Meerkat problem.
I see no issues with rhythmbox as far as importing anything.
Possibly the method and what you actually mean by this is a factor.

> I am using Maverick Meerkat, did the latest partial upgrade yesterday


---

### Post by cariboo on 2010-08-15
I have an issue, rhythmbox won't import files from an nsf share, it will import from the Music directory in my /home directory.

I believe the import from a share is a known bug.

---

### Post by Stoneface on 2010-08-16
> **mc4man said:**
> I see no issues with rhythmbox as far as importing anything.
Possibly the method and what you actually mean by this is a factor.
Well, when I go to music > import folder or file and select the folder or file from the pop-up menu to get the file or folder located in ~/Downloads it does not import anything. Putting folders or files directly in ~/music will load them automatically. The method of importing I tried is clearly not working. I clicked on Rhythmbox help to get some information on importing, but help would not open.

---

### Post by mc4man on 2010-08-16
while saw no issue on my desktop w/ impoting from within maverick or any other partition, did see issues on this laptop as you've described.

I think it may be the rhythmbox-ubuntuone-music-store that's causing it.
(too late to totally ck.
I completely removed that package in synaptic and importing started up again.

Maybe give that a try, if no go, then run this (slightly more will be removed than installed
```
sudo apt-get purge rhythmbox
```
followed by
```
sudo apt-get install rhythmbox
```

---

### Post by sinurge on 2010-08-16
I dont think you are completely right mc4man, i was having the same problem, i did a apt-get remove rhythmbox and the ubuntu-rhythmbox-ubuntuone-music-store was also removed. When i did a reinstall i did not get that in the list of files to be installed. Post that i started it and it works correctly.

Post this i did a reinstall of the rythmbox-ubuntuone-music-store program and then tried it works correctly now.

So i guess the steps are 
1. sudo apt-get remove rhythmbox
2. sudo apt-get install rhythmbox
3. sudo apt-get install rhythmbox-ubuntuone-music-store

So there is still a problem, i ran a dmesg | tail | grep "rhythmbox"
it did show a problem 

[ 9328.477658] rhythmbox[1847]: segfault at 30 ip 049ebf35 sp bfca2300 error 4 in libindicate.so.4.0.3[49e7000+d000]
[ 9751.230317] rhythmbox[3005]: segfault at 30 ip 013ebf35 sp bfd26240 error 4 in libindicate.so.4.0.3[13e7000+d000]

---

### Post by cariboo on 2010-08-16
When you use the purge option, it removes everything including the configuration files, The remove option, only removes the packages, and leaves the configuration files behind in /etc and your /home directory. Rhythmbox-ubuntuone-music-store, is a separate package and not a dependency of rhythmbox.

---

### Post by Longinus00 on 2010-08-16
> When you use the purge option, it removes everything including the configuration files, The remove option, only removes the packages, and leaves the configuration files behind in /etc and your /home directory. Rhythmbox-ubuntuone-music-store, is a separate package and not a dependency of rhythmbox.

Purge only removes configuration files from system folders, it won't touch anything in /home.

---

### Post by mc4man on 2010-08-16
> Rhythmbox-ubuntuone-music-store, is a separate package and not a dependency of rhythmbox. 

No but rhythmbox is a dep of the ..store which was the whole point of the purge and re-install

> sudo apt-get purge rhythmbox
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  rhythmbox* rhythmbox-plugin-cdrecorder* rhythmbox-plugins*
  [COLOR="Blue"]rhythmbox-ubuntuone-music-store*[/COLOR]


> Post this i did a reinstall of the rythmbox-ubuntuone-music-store program and then tried it works correctly now.

probably because the ...store plugin is disabled

> So there is still a problem, i ran a dmesg | tail | grep "rhythmbox"
it did show a problem - ect. ect. [COLOR="Blue"]libindicate.so.4.0.3[/COLOR][

I believe that to be totally unrelated to this issue - that 'crash' is related to the panel and probably occurs when  sometimes exiting rhythmbox (not always

---

### Post by mc4man on 2010-08-16
I don't actually use rhythmbox too much so the simplest thing did escape me...
The 'issue' occurs not whether the ...store package is installed, but whether the plugin is enabled or not.

At least here with it enabled only files or folders from ~/Music can be imported.
With it disabled they can be imported from anywhere on the machine

(I didn't realise the ..store was a plugin - never looked

---

### Post by kyleabaker on 2010-08-16
I've been seeing this issue off an on for a little while, even now with a completely fresh Ubuntu 10.10 x86_64 install.

1. Rhythmbox -> Music -> Import folder...
2. Open/select folder to import and click Open (I tried both opening the folder and just selecting it).
3. New music isn't imported.

Here is my temporary workaround for this.
1. Open Rhythmbox.
2. Open the music folder in Nautilus.
3. Drag-n-drop the music folder to the Music library in Rhythmbox and music successfully imports as expected.

I'm still not sure what causes this problem, but are you guys suggesting its caused by a plugin?

---

### Post by mc4man on 2010-08-16
> I'm still not sure what causes this problem,

Well, try opening rhythmbox -> edit -> plugins and making sure the 'Ubuntu One Music Store' plugin is disabled and see if that helps.

---

### Post by ktp on 2010-08-16
> **mc4man said:**
> Well, try opening rhythmbox -> edit -> plugins and making sure the 'Ubuntu One Music Store' plugin is disabled and see if that helps.

good thing that is the first thing I disable...along with few others.

---

### Post by Stoneface on 2010-08-17
> **mc4man said:**
> Well, try opening rhythmbox -> edit -> plugins and making sure the 'Ubuntu One Music Store' plugin is disabled and see if that helps.
I unplugged the Ubuntu One Music store as suggested et voila I could import folders again. Thanks a lot Mc4man! Hopefuly this buck will be resolved in the future. Will make a note in the bug report I filed.

---

