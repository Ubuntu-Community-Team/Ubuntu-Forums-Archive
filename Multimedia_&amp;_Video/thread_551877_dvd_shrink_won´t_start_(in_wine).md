---
title: "dvd shrink won´t start (in wine)"
date: 2007-09-15
forum: Multimedia &amp; Video
---

### Post by belias on 2007-09-15
hi, old story..dvd shrink installs, but won´t run (wine). i´ve read and tried everything for two days now. I do believe it has something to do with the quarts.dll, because after install, when it asks you to run shink, the lines in the command box go on forever with the following:

[PHP]belias@DEATHSTAR1:~$ wine Desktop/dvdshrink32setup.exe
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls"
fixme:advapi:CheckTokenMembership ((nil) 0x1291e0 0x34fe00) stub!

(THEN THE INSTALL INTERFACE STARTS, AFTER COMPLETING, AND SELECTING ¨RUN SHRINK¨,  THE FOLLOWING GOES ON FOREVER IN THE TERMINAL...)

{36b73882-c2c8-11cf-8b46-00805f6cef60}
fixme:quartz:Filtergraph_QueryInterface unknown interface {36b73882-c2c8-11cf-8b46-00805f6cef60fixme:quartz:Filtergraph_QueryInterface unknown interface {36b73882-c2c8-11cf-8b46-00805f6cef60}
fixme:quartz:Filtergraph_QueryInterface unknown interface {36b73882-c2c8-11cf-8b46-00805f6cef60}
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb41-f175-11d1-a392-00e0291f3959} not found
fixme:devenum:DEVENUM_ICreateDevEnum_CreateClassEnumerator Category {cc7bfb46-f175-11d1-a392-00e0291f3959} not found
fixme:process:IsWow64Process (0xffffffff 0x314f04) stub!
fixme:process:IsWow64Process (0xffffffff 0x314f04) stub!
fixme:process:IsWow64Process (0xffffffff 0x314f04) stub!
fixme:process:IsWow64Process (0xffffffff 0x314f04) stub!
fixme:quartz:Filtergraph_QueryInterface unknown interface {36b73882-c2c8-11cf-8b46-00805f6cef60}
fixme:quartz:Filtergraph_QueryInterface unknown interface {36b73882-c2c8-11cf-8b46-00805f6cef60}
fixme:quartz:Filtergraph_QueryInterface unknown interface {36b73882-c2c8-11cf-8b46-00805f6cef60}
fixme:quartz:Filtergraph_QueryInterface unknown interface {36b73882-c2c8-11cf-8b46-00805f6cef60}
f
[/PHP]

After this, none of the shrink startup .exes will get shrink to open.

---

### Post by mc4man on 2007-09-15
shrink is fairly easy to setup depending on what ver. of wine you have. A couple of ver. break it though it can be fixed by using different versions of quartz.dll
no matter what ver. of wine set windows version to nt 4.0 in winecfg 1st.
go to this link
[http://www.mrbass.org/linux/ubuntu/dvdshrink/](http://www.mrbass.org/linux/ubuntu/dvdshrink/)
and find the .dll zip, dl and extract the 3 dlls to system32 folder  (mfc42, riched20, quartz)
forget the guide, generally it's outdated
in winecfg libraries dll overrides set riched20 to native/builtin
then install shrink
if it doesn't run set quartz.dll to native/builtin
if it still doesn't run use another version of wine or find quartz.dll ver. 6.3.1.881

edit:uninstall shrink before starting

---

### Post by belias on 2007-09-16
mc4man thank you. Although i finally found the problem before I read you're post, i went ahead and used you're method too, just to play it safe. Turns out Nero 6 was the culprit..apparently there's some incompatibility in wine that totally stops shrink from running. 
Still have issues though..Decrypter and Image burn wont detect the usb burner...any ideas out there? The default linux burner does the job for now, but eventually decrypter's going to be needed again when someone decides to put a thousand vobs on a disk. 
Also if anyone know's of a linux substitute for the nero suite?

---

### Post by knahrvorn on 2007-09-16
> **belias said:**
> Also if anyone know's of a linux substitute for the nero suite?

I have found a lot of use in k3b. Not installed by default in Ubuntu, but it's in the repositories,

---

### Post by mc4man on 2007-09-16
Unfortunately I don't have a usb burner so i can't tell you if they'll work under wine. As far as imgburn I think it's the best build/burn prog. and use it all the time. It is very sensitive to the ver. of wine and needs different settings for the build and burn modes. I can post the methods if there's any further interest. Would be useful to know what ver. of wine your using and can shrink find your usb drive ? (put a dvd in drive and try open disk) note: win ver. in wine has to be nt 4.0 or higher
Assuming you can access a usb drive in wine and that your settings for imgburn in write mode are good you could try 1st inserting a dvd with data on it (movie, burned backup, whatever), let it mount and then open imgburn and see if you can find the disk/drive, if so eject and insert blank media keeping imgburn open
I would also recommend checking out K9copy. I only use it for ripping to a video_ts but it seems to offer alot and I think you can combo it with k3b

---

