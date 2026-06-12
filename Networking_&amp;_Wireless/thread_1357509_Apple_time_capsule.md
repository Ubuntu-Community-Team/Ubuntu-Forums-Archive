---
title: "Apple time capsule"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by mortuk on 2009-12-17
Hey all

I am trying to connect to an Apple time capsule in karmic koala. I have seen a few posts about it but none seem to help

[This]("http://ubuntuforums.org/showthread.php?t=670535") thread says to do the following

```
sudo mount.cifs //192.168.0.231/"Melon's Time Capsule"/Data /media/capsule -o pass=xxxx
```

This didnt work and kept giving me mount error 6 so I renamed the time capsule to 'timecapsule' and tried the following without spaces and 's

```
sudo mount.cifs //192.168.0.231/timecapsule/Data /media/capsule -o pass=xxxx
```

Still mount error 6, so tried a few variations until I got to

```
sudo mount.cifs //192.168.0.231/Data /media/capsule -o pass=xxxx
```

Which actually ran without error, plus it seemed to mount the folder. Go into /media/capsule and its empty :( also right click and properties and it seems to figure out the correct used / free space, but cant see any of the actual contents?

---

### Post by mortuk on 2009-12-18
Anyone?

Also noticed if I use fstab and mount it with write perms I can create files / folders, which will show up if I view the TC on another mac, but wont show up if I mount another linux machine.

I thought it might be file perms but the perms and owner are no different to the other files on there. Totally stuck, anyone got this working?

All the articles and posts I can find on it say to do the following method
```
sudo mount.cifs //192.168.0.231/"Melon's Time Capsule"/Data /media/capsule -o pass=xxxx
```
which just gives me mount error 6 everytime

---

### Post by hermans on 2009-12-21
> **mortuk said:**
> Hey all

I am trying to connect to an Apple time capsule in karmic koala. I have seen a few posts about it but none seem to help

[This]("http://ubuntuforums.org/showthread.php?t=670535") thread says to do the following

```
sudo mount.cifs //192.168.0.231/"Melon's Time Capsule"/Data /media/capsule -o pass=xxxx
```This didnt work and kept giving me mount error 6 so I renamed the time capsule to 'timecapsule' and tried the following without spaces and 's

```
sudo mount.cifs //192.168.0.231/timecapsule/Data /media/capsule -o pass=xxxx
```Still mount error 6, so tried a few variations until I got to

```
sudo mount.cifs //192.168.0.231/Data /media/capsule -o pass=xxxx
```Which actually ran without error, plus it seemed to mount the folder. Go into /media/capsule and its empty :( also right click and properties and it seems to figure out the correct used / free space, but cant see any of the actual contents?

I have the same problem! I cant see any contents of my TimeCapsule, but I can see the space properties of it... any ideas to resolve this problem?
thnx

---

### Post by mortuk on 2010-04-07
I still haven't solved this, any ideas?

---

### Post by sloosley on 2010-04-08
I'm having a similar problem, when I try to mount my Time Capsule. 

I issue the following command in terminal: 

[FONT="Courier New"][INDENT]sudo mount.cifs //192.168.1.1/My Time Capsule/Ubuntu /media/timecapsule -o pass=mypassword[/INDENT[/FONT]]

Terminal promptly gives me a 
[FONT="Courier New"][INDENT]> [/INDENT][/FONT]
And, if I switch to /media/timecapsule the directory is empty.

I'm a clueless newbie, so please temper your responses :)

---

### Post by AVeryLongNickname on 2010-05-14
Yeah.. I have the exact same problem, and have had it for a while now.. not found any way around it though :(

Anyone got any ideas at all? :)

---

### Post by peap on 2010-05-21
I'm using this fstab entry to successfully mount my TimeCapsule using Lucid server.

//10.0.1.1/TimeCapsule /media/timecapsule cifs password=password,noserverino,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

---

### Post by Bryan7675 on 2010-07-02
This is the page I followed to connect my time capsule and lucid.

[http://www.organicdesign.co.nz/Connect_Ubuntu_system_to_a_time_capsule]("http://www.organicdesign.co.nz/Connect_Ubuntu_system_to_a_time_capsule")


sudo mount.cifs //10.0.1.1/Time_Capsule/ /media/capsule -o pass=xxxxxxxxx

The hardest thing for me was the name after the IP address.  Using AirPort Utility select the time capsule, and select manual setup.  The very top row of icons, one is labeled "Disks" selected it.  Now we have selected the Disk icon, make sure you are on the Disks tab, and it should show you a small folder tree; my top option is Time Capsule Disk, Then below that it says Time_Capsule, select that one.  Now to the right you have a name field you can change.  I changed mine so it still has caps, but I removed the space and added and under score.  This is the name that should be placed behind the IP address.

I hope this helps some of you out their.

Now I still having troubles getting the time_capsule to automatically mount when the system turns on.  Any info would be greatly appreciated.

---

### Post by Scuzzlebud on 2011-02-17
Hi,

I understand this is rare problem, but I installed Mythbuntu on an old Dell Inspiron Laptop a few days ago to use it as a home media center. Thus, I wanted to mount my TimeCapsule from the system so to be able to stream the video from a hdd attached to the TC. 

I have to say that I was hardly able to install any programs since I am a spoiled Mac user :>
I don't know how to make an actual program out of the downloadable source code of a twitter app, for instance.

Now I finally managed to follow the instructions found in an archived thread ([http://ubuntuforums.org/showthread.php?t=670535](http://ubuntuforums.org/showthread.php?t=670535)) and (allegedly) successfully mounted my TC. I don't know how to edit fstab so I first used the other method, like,

sudo mount.cifs //192.168.178.22/"Capsule"/ /media/capsule -o pass=password

which persistently returned an error, so I tried

sudo mount_afp afp://root:"Pass"@192.168.178.22/EXT/Data /media/capsule

which seemed to have worked. "EXT" is the actual folder on my TC which I learned has to be entered INSTEAD of just the name of the TC. 
Well, since this looked like it had worked (when trying again, I got an error telling me the drive was already mounted on /media/capsule), the folder /capsule I had created before wasn't there any more and no data showed up.
Now, after a night of sleep, I tried it again using

sudo mount.cifs //192.168.178.22/CapsuleFolder/ /media -o pass=password

which got me into my desired folder. I'm currently streaming video, but several questions are still unanswered for me (apart from the work I see in front of me because I think I finally really have to learn the general system commands).

1) I don't have writing privileges. Is it right I can get them by using an fstab command?
2) How can I use the aforementioned fstab to not have to mount the TC every time again, which means: How can I edit any friggin' file on my system. Is it possible without downloading much additional software (I only installed mythbuntu 10.04 via CD and run the Updater which installed a bunch of updates, then smbfs and smbclient)?
3 (which actually belongs in another section) The OS seems to be pretty slim. Since there only is Firefox showing up in the network category of xfce, I assume I need to install anything I want to use other than a basic file manager (thunar) and a browser, right?

You see, I'm a complete noob since I aborted my several tries to understand Linux starting in 1999...so thank you very much in advance!
Max

---

### Post by GeneRalf on 2011-04-26
Hi,
I actually had the same issue until I figured out, that I am having a different Username on the time capsule than on my Linux.

sudo mount.cifs //Networkaddress/(Name of the time capsules disk)/ /media/foldername -o username="username" pass=password 

Please note, 
>Networkaddress is the IP you can reach the timecapsule within your network
> do not use the () and also not the TimeCapsules name but the HDD installed in the time capsule
> foldername can be anything what you have created inside media folder
> username, use " " in case you have something like "John Doe"

So bottomline, the description of all members above are fine but missing the USERNAME... may this helps for you too.

cheers
GeneRalf

---

### Post by gulernhagen on 2011-09-26
A million thanks bryan for your post, I've been at this for days trying different guides and such, no one made it clear that I had to use the name given to the HD and not the Time Capsule name before. 

If anyone else is having troubles and want to follow bryan's solution, remember that you first need the proper software, which you can get by opening the terminal (Applications>Accessories>Terminal) and typing the following:

sudo apt-get install smbfs

press enter, type in your password(won't show up when you type), press enter again. When it asks you if you want to install, press the letter "y" and then enter again.

After that type:

sudo apt-get install smbclient 

And repeat the same process as you did with the previous software.

After that you need to create a mountpoint, that is done by typing the following in the terminal:

cd /media

Press enter and then type:

sudo mkdir capsule

Press enter.

What you've done is create a folder in the "media" folder, which can be reached by clicking Places>Computer>File System>media. If you want to give the folder a different name just type something else instead of "capsule" in the line "sudo mkdir capsule".

After that just follow bryan's instructions and your Time Capsule hard drive should pop up on your desktop!

There might be some errors in my description of how the software installation process transpires, I'm very new to Ubuntu and haven't really memorized it yet, good luck!

---

