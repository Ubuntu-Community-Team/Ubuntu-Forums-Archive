---
title: "Edimax 7811 /  Realtek 8192CU"
date: 2012-12-02
forum: Networking &amp; Wireless
---

### Post by iamrandy on 2012-12-02
i just got this edimax 7811un wireless adapter and it says connection established but i get a dns error here is some things i've been able to compile and i have 12.04 please help this is so frustrating[ATTACH][ATTACH][ATTACH]228131[/ATTACH][/ATTACH][/ATTACH]

---

### Post by ahallubuntu on 2012-12-02
Your Edimax wireless card uses a Realtek 8192CU chipset.  This chipset has known bugs in Ubuntu 12.04 LTS and 12.10.

The common solution is to download the newest driver from Realtek's website, build the driver, blacklist the old driver, and enable the new module to load at each boot-up.  Details here in my answer #2 in the thread below (I have tested this with my 8192CU cards in both 12.04 and 12.10):

[http://ubuntuforums.org/showthread.php?t=2076315](http://ubuntuforums.org/showthread.php?t=2076315)

---

### Post by chili555 on 2012-12-02
A 10.42.0.xx IP address is typical of an ad-hoc computer-to-computer connection sharing arrangement. It is usually the result of filling in settings by clicking the Network Manager icon and selecting 'Create New Wireless Network...' Is that what you did? Is your wireless set to Infrastructure or Ad Hoc? Please see attached. Disregard the MTU setting.

I suggest you set to Infrastructure, wipe out all settings and let Network Manager discover your router and connect all by itself.

---

### Post by iamrandy on 2012-12-02
i have downloaded the files but that's as far as i can get i am not very good at this but please any help is much appreciated thank you

---

### Post by chili555 on 2012-12-02
> **iamrandy said:**
> i have downloaded the files but that's as far as i can get i am not very good at this but please any help is much appreciated thank youWith the utmost respect to my colleague ahallubuntu, I suggest you sort out the Infrastructure issue first and *then* decide if you need a new driver.

---

### Post by iamrandy on 2012-12-02
ok i did the infrasructure thing and it keeps asking me for the password over and over

---

### Post by chili555 on 2012-12-02
> **iamrandy said:**
> ok i did the infrasructure thing and it keeps asking me for the password over and overOK, now I'd try the newer driver.

ahallubuntu?

---

### Post by iamrandy on 2012-12-02
like i said i downloaded the drivers but i have no idea what to do with them

---

### Post by ahallubuntu on 2012-12-02
> **iamrandy said:**
> i have downloaded the files but that's as far as i can get i am not very good at this but please any help is much appreciated thank you

After you download (should be just one file zip to start that gets expanded to many), double-click on the zip file you downloaded and say "extract."  That should create a directory in your home Downloads directory.  The current version is called "RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105" but that will change (for future readers of this thread) as Realtek updates the driver in the future.

Anyway - at this point you have to start up a program in Ubuntu called "Terminal."  This is kind of like "DOS" command window if you ever used old computers (before Linux), but there's not much to type.  Just a few lines.

You can search Ubuntu for "terminal" and double-click on the first result to open a terminal.  Then type

```
cd ~/Downloads/RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105/
```

(again, that name at the end will change - depends on what the name was of the file you downloaded).

then type in the terminal window:

```
chmod 755 ./install.sh
```

(hit Enter)

then type

```
sudo ./install.sh
```

(hit enter and and type your password)

That should build the new driver.

Finally, you have to blacklist the old driver files and add the name of the module (driver) you just built to the modules file, so wireless is always enabled when you turn on the computer.  The instructions for editing those files are give in that same link I gave you before:

[http://ubuntuforums.org/showthread.php?t=2076315](http://ubuntuforums.org/showthread.php?t=2076315)

If you are having issues, where are you getting exactly stuck?

---

### Post by iamrandy on 2012-12-03
ok this is what i tried and this is what happened

---

### Post by iamrandy on 2012-12-03
sorry this is the attachment[ATTACH]228173[/ATTACH]

---

### Post by ahallubuntu on 2012-12-03
You seem to have downloaded two versions of the driver?  Where did the one ending in "0726" come from?

In the terminal, type:

```
cd ~/Downloads
ls
```

Is there a file in that list that ends with ".zip" ?

If you see the file "RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip" in the list, type

```
unzip RTL8192xC_USB_linux_v3.4.4_4749.20121105.zip
```

which should create the directory "RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105" in the Downloads directory.  Then type:

```
cd RTL8188C_8192C_USB_linux_v3.4.4_4749.20121105
```

Don't type the "cd" command unless that directory name exists in your listing.  Otherwise, it will fail.  Don't try the "install.sh" stuff unless you can see it in the directory you are in.  Type "ls" in the terminal to see the list of files in the current directory.

I do see the correct one in your attachment but I'm not sure if it is unzipped or not.

---

### Post by iamrandy on 2012-12-03
ok this is what happened[ATTACH]228176[/ATTACH]

---

### Post by steeldriver on 2012-12-03
Linux filesystems are case sensitive - the directory is **rtl**XXXX but you are typing **RTL**xxxx

You can save yourself a lot of effort by using TAB completion - just type the first few characters e.g. rtl8192 and then press the TAB key... the shell will fill in the rest of the name for you

---

### Post by ahallubuntu on 2012-12-03
Or, after you do the "ls" highlight the name of the file you wish to unzip, then right-click on it and choose "copy."  Then right-click "paste" after you have typed "unzip."

---

### Post by iamrandy on 2012-12-03
ok now i got this sorry i'm so bad at this but thank you for being so patient i appreciate it big time[ATTACH]228178[/ATTACH]

---

### Post by ahallubuntu on 2012-12-03
That's the wrong file to unzip.  You seem to have downloaded an older one and a newer zip file.  You want to unzip the done that ends with "20121105.zip" .

FYI, the zip command you typed is telling you you had already unzipped this file and the files in it already exist.  Do you want to replace them?  Probably no need - hit Ctrl C to cancel this command.  Again, you want the newer one that ends in "20121105.zip" because that is the newest Realtek driver, the one most likely to work.

---

### Post by iamrandy on 2012-12-04
ok now this is what i have[ATTACH]228221[/ATTACH]

---

### Post by ahallubuntu on 2012-12-05
Downloads has a capital "D" .  It is important.  If you don't use the capital "D" for "Downloads" it's not going to work.  Can't you copy-paste these lines exactly instead of just re-typing them?

---

### Post by iamrandy on 2012-12-05
no for some reason nothing happens when i right click in the terminal

---

### Post by iamrandy on 2012-12-05
ok i think i got it what next[ATTACH]228248[/ATTACH]

---

### Post by iamrandy on 2012-12-05
i know i'm not the best at the terminal and all this language but if someone could please help me on this i would greatly appreciate it and it would save me from calling a geek

---

### Post by iamrandy on 2012-12-06
ok so now its asking me all these questions and i'm sure i messed something up[ATTACH]228276[/ATTACH]

---

### Post by iamrandy on 2012-12-08
ok i got it to install now i'm having trouble blacklisting please help

---

### Post by iamrandy on 2012-12-08
[ATTACH]228378[/ATTACH]sorry forgot this

---

### Post by chili555 on 2012-12-08
Please try this:```
sudo su
echo "blacklist rtl8192cu" >> /etc/modprobe.d/blacklist.conf
modprobe -r rtl8192cu
exit
```Proofread each step very carefully before you press Enter. Every little / and . and " must be exactly correct. Each line above is a separate command, followed by Enter. If in doubt, stop and ask first.

---

### Post by iamrandy on 2012-12-08
was this right[ATTACH]228382[/ATTACH]

---

### Post by chili555 on 2012-12-08
Looks fine! Now is your wireless working?

---

### Post by iamrandy on 2012-12-08
yipee ki yi yay you know the rest. that's exactly why i use these forums you guys are awesome thank you so much for your knowledge and patience with us young padawans

---

