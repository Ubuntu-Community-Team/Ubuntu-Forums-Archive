---
title: "trouble sharing folders across LAN"
date: 2009-10-05
forum: Networking &amp; Wireless
---

### Post by pjstock on 2009-10-05
Hello.
I posted this problem on a Linux Forum but got blown away by suggestions (probably very good suggestions by very kind experts who were trying to be helpful) like:

sudo mkdir /mnt/share
sudo mount -t cifs -o username=<user>,password=<pass> //<ip>/<share> /mnt/share

Yikes! this is why I got out of computer science 30 years ago.

So, I thought I would try it here in the hope of finding a simpler solution.

I know this issue is covered in many threads, but having read them, I am still failing.

Here's my situation.

1. My Windows XP laptop (call it XP1) failed last week, on a Blue Screen error.
2. Fed up with WIndows, I am ready to just convert it to Linux (Ubuntu.)
3. First though (as the Ubuntu install is suggesting using 100% of the HDD and I fear that might mean wiping out whatever is there) I would like to backup some key files.
4. Easiest way to do that would be over our LAN, to either another windows machine (WXP2) or another Ubuntu machine (call it Ubuntu 2, which has been running Ubuntu and crossing the LAN fairly effortlessly since I set it up -- though more by chance than knowledge apparently -- about 6 months ago.).
5. I have been booting the laptop to Ubuntu from the install CD and running it without doing the install.
6. I have set up file sharing on XP1 and Ubuntu2 and can move files between these two.
7. I have tried to set up file sharing on the laptop and have installed Samba but, even though I can see the other machines on the LAN, I do not seem able to write files to them. Nor can I see the Laptop (running CD Ubuntu) from another machine.
8. Samba (on the laptop) does not seem to allow me to specify a machine across the network for shaing.
9. when I do Places > Network I see the other machines on the LAN but when I click through to them I get nothing, no folders showing.

What am I doing wrong. 
I can't believe this should be this complicated. 
Is there something about running Ubuntu only from CD that is preventing me from file/folder shaing, either by pulling files from it or pushing files to the other machines.

peter

---

### Post by Roasted on 2009-10-05
Let's take a few steps back and analyze what you're trying to do. From there, I'm sure we can get you rolling again in the proper direction.

Ultimately, you have an Ubuntu desktop and a laptop, which the laptop sounds up in the air between Ubuntu and XP. However, if there's ever going to be a Windows machine on your network, let's work with Samba. I personally love having Samba rigged up on my desktop because I can so easily access it from my Mac laptop and any Windows machine in the house.

There's a few key things to remember here. When you are dealing with Samba, there must be a Samba user existent. On top of that, this user should also be a local user on your Ubuntu machine.

AKA - I am Jason. Jason is an account on my Ubuntu machine, and he's also a Samba user as well. 

How about you go to terminal and run "nano /etc/samba/smb.conf" and paste what it is here. Then we can look at it and see if things are goofy or not.

---

### Post by pjstock on 2009-10-05
thanks Jason,
after some fiddling with Samba I seem to have managed (despite myself and my Linux ignorance) to have added and enabled Root as a Samba user, added the "disk" as a shared thingee under Samba. and it magically appeared in my Windows box's Network Places. 
I am presently offloading the stuff I want to save.

Now, to make this whole process a lot less "cross fingers and pray" and to not waste time like yours necessarily, I expect I should take a few hours and read up on the basics of Linux/ubuntu.

Now, while I have you maybe I could bug you for this next issue. The only reason I would not replace Win XP with Ubuntu would be if I could NOT make the current wifi adapter work (the type of which I cannot confirm without rebooting which would wipe out the Samba setup I have done so far.)

- can I confirm the type of wifi adaptor presently in the laptop via Ubuntu from CD?
- how would I know if drivers exist for it for Linux/Ubuntu?,
- and finally, if drivers exist, how would I make that driver "function".

Peter

reading the Dell X300 specs, the wifi adaptor should be:

.Standard Intel® Wireless 2200 WLAN (802.11b/g) Mini-PCI, Wi-Fi® compatible;

and Intel appears to have a driver for it.

Now, just have to figure out how to install that driver on a Linux laptop.

---

### Post by Roasted on 2009-10-05
The beautiful thing about Linux is it has a great hardware detection system. To date, the only drivers I've ever installed were video card drivers. Everything else, including the wireless card in my laptop I passed off to my girlfriend (the infamous Realtek RTL8187B) is even supported through the Linux kernel now.

What I suggest is that you boot to the LiveCD and try to connect to your wireless network while running on the LiveCD. There's only so much I personally know about drivers in Ubuntu because, to be quite frank, I rarely ever have to deal with them.

I am however interested in helping you more with Samba and making sure it works properly. It makes me a little nervous that you spoke about root, simply because Ubuntu by nature tends to shy away from the root account and they actively keep it hidden and disabled.

Tell me a little bit more about what YOU want out of a file sharing system at your home network, and maybe we can iron something out that's more concrete and up your alley.

I'll tell you what I do with Samba, and you can decide from there if anything I use it for is the way you want to use it for.

My situation:

After my brother had two hard drive failures, resulting in lost data, I decided to rig up two spare 250gb SATA drives in my system and share them out with Samba. Once a day (4 am) users automatically synchronize their my documents folder to their password protected Samba share on my system using third party Windows software (SyncBack SE) to kick all of the data to my server.

Each user has a Samba account and a password.
Each user has a dedicated folder that only they can open, using their samba account name and password.

This enables the backed up data on my system to be *as* secure as it is on the home system. Since only my brother can get into his computer, he also is the only one who can get into his backed up data. You can open permissions wider if you want, like I did with MY particular share.

My samba account maps to /home/jason (me), so I can hit my documents, music, videos, etc from anywhere on the LAN.

How do I connect? Well, my server name is Area51. So on the XP/Vista/Windows 7 machine (I've tested it with all 3) I go to start - run - \\Area51 and I get prompted with a login box. From there, I type in jason (samba account) and type in my password. Presto - instant access.

You can also have Windows remember this password by selecting "remember password" on the checkbox.

Don't worry about "wasting my time". This is a support forum and a lot of us here spend time helping others out of personal interest. I am by no means an expert on Samba. I just have a deep interest in it since I run a Samba server at home for the entire purpose of being an all around user friendly file server.

If you decide you want to dig a little deeper in understanding Samba and Linux and whatnot, we can continue the conversation here by showing me the output of "nano /etc/samba/smb.conf" from terminal and pasting it here, along with telling me more about what you plan to achieve from a home file server. How many users? Just you? Are they backing up for redundancy? Mapping drives in Windows? 

If not, we can call it case closed. Otherwise, hit me back with that other info. :guitar:

---

### Post by pjstock on 2009-10-05
I will gladly take you up on your kind offer of Samba help. Once I figure out how to make wifi work on this laptop.

once I get that sorted, I'll come right back for LAN setup help.

(for the moment, when running off the Live CD setup, once I unplug my ethernet, I lose the Internet access and don't see anything that would suggest there the laptop as is is seeing the wifi signal here. so, it doesn't appear to be automatic.)

Peter

---

### Post by Roasted on 2009-10-05
Go to terminal and run "ifconfig"

Paste the output here.

Also, in terminal, run "lspci"

Also paste that here.

---

### Post by pjstock on 2009-10-07
Jason.

I am back.
the laptop is working pretty well. you were correct -- the wifi was recognized automatically.
Now though I have wrecked my other Ubuntu installation, on a desktop. I interupted an upgrade to 9.04 and it is stuck. I have been advised to just reinstall 9.04 from CD.

BUT, I need to back up some critical documents first. But, having booted from CD on this desktop, I cannot for the life of me get access to these folders across the LAN.

I have installed SAMBA, I have done the smbpasswd -a and -e thing (do I need a user name? or can I leave it blank for this running off the CD?)
I then set up the folders as Shares in Samba and... nothing. while I can see the machine from the other machines, I cannot access the folders to copy them off.

Nor can I see the other target machines from this machine. I click on Network and I see WIndows Network and then three machines across the LAN but when I click through to them I don't see any folders or anything. just blank.

any suggestions?

---

### Post by Roasted on 2009-10-08
You're asking a very unique question, based on the fact you're trying to launch a temporary Samba network from a LiveCD - something I'm not positive will work.

Instead, I would still utilize the LiveCD but also grab an external hard drive and plug that in. You should be able to recognize your internal hard drive (with the failed install) and the external, and be able to copy/paste files accordingly.

I honestly think you will be better off doing this. Samba on a LiveCD, although it may work in theory, sounds tricky.

Do you have your partitions split? Do you have root and home on different partitions? Reason I ask is, if you split your partitions up, you can redo an Ubuntu install without losing the contents of your home directory.

My partition scheme is set up as: 

1gb Swap
20gb Root
390gb (remainder of drive) Home

Then when I install Ubuntu, I mount the 1gb spot to swap area, 20gb to /, and the 390gb as /home. Then when I upgrade to a new version of Ubuntu and I do a fresh install, I format root ( / ), but I make sure I don't have /home checked to format. I still mount that partition with the file system (I have it as EXT3) and the mount point as /home, but I just make sure it's not set to format.

Did you ever consider that? Once you grab the data off of the drive, it might not be a bad idea, especially since you have to build from ground-up on a new install anyway.

---

### Post by pjstock on 2009-10-09
good suggestions, thank you.
rather than fiddle with Partitioning with sensitive data (I will try that another time) my plan now is to stick a separate 20Gb HDD in the machine, install Ubuntu 9.04 to that and then use the 250G HDD just for data.

my problem now is that having disabled the 250Gb HDD temporarily as a precaution, and plugged in the spare 20Gb HDD I had lying around, I am getting a Cannot Mount Volume Message.

maybe if I just go for it and install Ubuntu, it will reformat or something and clear this up?

Peter

Hello Again.
well, here's the latest.
I stuck in a blank 30Gb hard drive and installaed Ubuntu 9.04 to it. 
that seems to work.
I then added the old 250Gb with the data I was trying to protect as a Slave Drive.
That seems to have been recognized.
Now though when I log in as the newly installed user (Julie) I cannot seem to access the old main user (called "lola2")
there were two users on the old 8.04 system. Lola2 and Peter.
From Julie and I get at the Peter files and folders.
but I the Lola2 folders all have Xs beside them and I am being told I do not have permission.

so it appears I have saved the data. but in the process I have thrown away the key?

how can I patch things up so that Julie (the only  current User Account on this newly re-installed system) can access the old Lola2 files and folders.

---

### Post by Roasted on 2009-10-09
Hmm, navigate to the directory in terminal and run

ls -l

And paste the output here.

Example - If I want to find the permission settings of /media/storage, I CD to /media and run ls -l, and storage would pop up below.

---

### Post by pjstock on 2009-10-09
Hi

Errrh, how do I navigate to that folder in terminal?
I kind of remember CHDIR and CD from my old very brief 70s dabble with Unix. But when I do "cd" in terminal, I get:

julie@julie-desktop:~$ cd 


the big HDD is showing as "248.5 GB Media" but I can't imagine that is a name that Terminal is going to like.

it is a physically distinct HDD right?

I am also trying to understand this groups and permissions suggestion. Yikes!

if the files under the Lola2 folder on the "248.5 GB Media" were locked to Lola2 user when I crashed the upgrade to 9.04, is it even possible for a new user (Julie) to be allowed at it?

can't I just log in as Root somehow and magically change the permissions on Lola2 folder? (I tried to login as Root -- a beginners Ubuntu manual suggested that was possible) but

OK, I remembered DIR to see where I was. sort of.

julie@julie-desktop:~$ cd
julie@julie-desktop:~$ cd..
bash: cd..: command not found
julie@julie-desktop:~$ cd media
bash: cd: media: No such file or directory
julie@julie-desktop:~$ dir
Desktop    examples.desktop  Pictures  Templates
Documents  Music	     Public    Videos
julie@julie-desktop:~$ cd /root
bash: cd: /root: Permission denied
julie@julie-desktop:~$ cd 248.5
bash: cd: 248.5: No such file or directory
julie@julie-desktop:~$ 

now I am lost again.

---

### Post by CharlesA on 2009-10-09
Where did you mount the other drive? It's probably in media or mnt.

cd /media/home/username/whatever

Remember your spaces. cd.. won't work, while cd .. will. :)

EDIT: I've logged "in" as root using sudo -s from a terminal screen. That's not really needed tbh, since you can just use:

```
sudo chmod 755 /folder/path/goes/here/
```

---

### Post by pjstock on 2009-10-09
here's what I have been stumbling with lately.

julie@julie-desktop:~$ ls
Desktop    examples.desktop  Pictures  Templates
Documents  Music             Public    Videos
julie@julie-desktop:~$ cd public
bash: cd: public: No such file or directory
julie@julie-desktop:~$ cd documents
bash: cd: documents: No such file or directory
julie@julie-desktop:~$ cd
julie@julie-desktop:~$ cd ?
bash: cd: ?: No such file or directory
julie@julie-desktop:~$ cd  
julie@julie-desktop:~$ cd /media/home
bash: cd: /media/home: No such file or directory
julie@julie-desktop:~$ cd /mnt/home
bash: cd: /mnt/home: No such file or directory
julie@julie-desktop:~$ 

I have no clue what is going on.

thanks Charles.

How do I confirm where I mounted the drive?
I just plugged it in and Voila! it magically appeared under Places.

---

### Post by CharlesA on 2009-10-09
Ok, can you post the results of ls -l  /media

EDIT: Is the media listed on the desktop as well?

---

### Post by pjstock on 2009-10-09
ahah!
getting there.

cd /media/disk/home

gets me "over there"

---

### Post by CharlesA on 2009-10-09
> **pjstock said:**
> ahah!
getting there.

cd /media/disk/home

gets me "over there"

Ok, what's listed in the home directory?

run ls -l and post the results please.

---

### Post by pjstock on 2009-10-09
Darn, no.

that cd /media/disk/home 

left me on the 20Gb HDD side.
how do I get over the fence?

here's what ls -l /media yields

julie@julie-desktop:~$ ls -l /media
total 16
lrwxrwxrwx  1 root root    6 2009-10-09 12:24 cdrom -> cdrom0
drwxr-xr-x  2 root root 4096 2009-10-09 12:24 cdrom0
drwxr-xr-x  2 root root 4096 2009-10-09 12:24 cdrom1
drwxr-xr-x 21 root root 4096 2009-10-06 08:37 disk
lrwxrwxrwx  1 root root    7 2009-10-09 12:24 floppy -> floppy0
drwxr-xr-x  2 root root 4096 2009-10-09 12:24 floppy0
julie@julie-desktop:~$

---

### Post by CharlesA on 2009-10-09
Ok. Do you have "248.5 GB Media" somewhere on the desktop? I know you said it was in the places menu.

---

### Post by pjstock on 2009-10-09
under Properties of Lola2 on the 250GB HDD

Location: /media/disk/home
Volume: 248.5 GB Media

under Properties of the Julie folder (the current only user) which is on the 20Gb HDD I just reinstalled 9.04 on

Location: /home
Volume: unknown

Yes, there is a 245.8 GB icon on the desktop

Charles,
I must have mistyped something a few steps back.
I am now seeing the following in Terminal:

julie@julie-desktop:~$ dir
Desktop    examples.desktop  Pictures  Templates
Documents  Music	     Public    Videos
julie@julie-desktop:~$ cd /media/disk/home
julie@julie-desktop:/media/disk/home$ dir
lola2  peter
julie@julie-desktop:/media/disk/home$ ls -l
total 8
drwxr-xr-x 45  1001 upubuntu 4096 2009-10-07 12:09 lola2
drwxr-xr-x 36 julie julie    4096 2009-10-06 16:47 peter
julie@julie-desktop:/media/disk/home$

---

### Post by CharlesA on 2009-10-09
> **pjstock said:**
> Yes, there is a 245.8 GB icon on the desktop

~~~~~

> **pjstock said:**
> Charles,
I must have mistyped something a few steps back.
I am now seeing the following in Terminal:

julie@julie-desktop:~$ dir
Desktop    examples.desktop  Pictures  Templates
Documents  Music         Public    Videos
julie@julie-desktop:~$ cd /media/disk/home
julie@julie-desktop:/media/disk/home$ dir
lola2  peter
julie@julie-desktop:/media/disk/home$ ls -l
total 8
drwxr-xr-x 45  1001 upubuntu 4096 2009-10-07 12:09 lola2
drwxr-xr-x 36 julie julie    4096 2009-10-06 16:47 peter
julie@julie-desktop:/media/disk/home$


Ok. run this command:

sudo chown -R julie:julie /media/disk/home/lola2

That'll make you owner and you should be able to access the device to pull any data off of it.

---

### Post by pjstock on 2009-10-09
thanks for your patience.

I am installing Gparted now and will try these steps.
I'll report back once I am done.
Peter

errrh. device name is like:

/dev/sdb1

or just the "sdb1"?

---

### Post by CharlesA on 2009-10-09
Didn't see that you were able to get to the folder where the drive was mounted. There's no need for gparted now.

Run the command in my previous post and that should let you access the data.

If you are going to edit the fstab file, you'd need to add it as /dev/sdb

---

### Post by pjstock on 2009-10-09
Charles

I am not clear on this step:

sudo nano /etc/fstab
add this to the end:
/dev/sdax (tab) /lola (tab) file system (tab) 0 (tab) 0

when you say: "add this to the end" do you mean these two lines should be one long command?
i.e.
sudo nano /etc/fstab /dev/sdax (tab) /lola (tab) file system (tab) 0 (tab) 0

> **CharlesA said:**
> Didn't see that you were able to get to the folder where the drive was mounted. There's no need for gparted now.

Run the command in my previous post and that should let you access the data.

If you are going to edit the fstab file, you'd need to add it as /dev/sdb


Charles,
this command?

sudo chmod 755 /folder/path/goes/here/

does it matter that I unmounted the 248.5gb drive and started to do the first two commands from your bigger post?
sudo mkdir /lola2
sudo cp /etc/fstab /etc/fstabbk

> **CharlesA said:**
> Didn't see that you were able to get to the folder where the drive was mounted. There's no need for gparted now.

Run the command in my previous post and that should let you access the data.

If you are going to edit the fstab file, you'd need to add it as /dev/sdb

do I have to re Mount the 248.5 drive that I unmounted?
if so, it doesn't seem to want to mount when I right click and Mount.

---

### Post by CharlesA on 2009-10-09
> **pjstock said:**
> Charles

I am not clear on this step:

sudo nano /etc/fstab
add this to the end:
/dev/sdax (tab) /lola (tab) file system (tab) 0 (tab) 0

when you say: "add this to the end" do you mean these two lines should be one long command?
i.e.
sudo nano /etc/fstab /dev/sdax (tab) /lola (tab) file system (tab) 0 (tab) 0

Do you know the file system of the other drive? You'll need that for the next step.

sudo nano /etc/fstab [enter]

Once in nano you should see the list of devices and where they are mounted.

This is what my fstab file looks like:

```
  GNU nano 2.0.9                       File: /etc/fstab

# /etc/fstab: static file system information.
#
# Use 'vol_id --uuid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda1 during installation
UUID=9dd8f03b-463d-4af1-89a1-8d8e8fe965e1 /               ext3    relatime,errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=57762ea2-4181-4b30-8893-66cddb617683 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
#mount raid array
UUID=3209ca5b-103c-46f2-85ea-170d93259a7e       /array  ext3    defaults        0       0
#mount external usb drive
UUID=9d9b6106-ce83-4634-8b82-0ff304f3e855       /sync   ext3    defaults        0       0
```You can replace the UUID=xxxxx with /dev/sdb1. It'll look like this:

```
/dev/sdb1       /lola   ext3    defaults        0       0
```I'm not sure what file system is on the other drive, but you can replace ext3 with whatever it's formatted as. e.g., ntfs, ext2, etc.

EDIT: Sorry I think I took long way of doing things, since it was already mounted. Could try a reboot and see if the drive is mounted back in /media/disk/home. Then run the chown command from there.

Sorry I'm still kinda new to Linux so I'm still getting the hang of things.

---

### Post by pjstock on 2009-10-09
Charles,

good suggestion the reboot.
on reboot the 248.5 popped right up again.

and "sudo chown -R julie:julie /media/disk/home/lola2" seems to have done the trick.

many thanks for your help and patience.

Peter

---

### Post by CharlesA on 2009-10-09
You are welcome, glad to help. :-)

---

### Post by pjstock on 2009-10-09
Charles.
last question. I promise.
any idea why I would not be able to Create New Folder on the 248.5GB drive?
I would like to reorganize some of the legacy folders that were left over from the failed 9.04 upgrade and just make it a clean data drive.

are there some permissions that "Julie" is still lacking?

I seem to be allowed to Create Folders below the Lola2 and Peter level, but not above...

---

### Post by CharlesA on 2009-10-09
> **pjstock said:**
> I seem to be allowed to Create Folders below the Lola2 and Peter level, but not above...

Those are the roots of your drives I believe. Everything above them is owned by root.

To create folders there you need to use sudo.

What are you trying to create?

---

### Post by pjstock on 2009-10-09
Originally I had Ubuntu 8.04 running on that big 248.5G drive. and created two users on it -- Lola2 and Peter.
over the course of a few months use, we created a bunch of files and documents.
then I crashed the upgrade stranding those two user folders on the 248.5Gb drive.
then so as not to screw that data up (I just didn't know what a 9.04 install would do, I wasn't sure it would recognize the original install and protect it) I used that physically separate 20GHb HDD to intall 9.04.

now, all the Ubunut 8.04 system stuff on the 248.5 GB drive is basically dead and useless and just taking up space.
I really only need to use that drive as a storage location. 
I would like to clear out all that system stuff, or maybe tuck it into a folder down low and out of the way for now.

see what I mean?

---

### Post by CharlesA on 2009-10-09
I'm not quite sure how it's mounted tbh, but anything that is above that folder (lola2 and peter) is part of the current install (or at least I think that's how it is)

I would suggest opening those folders in the file browser and seeing how big they are. They way you'll know if you can copy them to the 20gb drive and format the larger one or not.

---

### Post by pjstock on 2009-10-15
Jason,

any chance I could now get your help setting up Samba and filesharing across my little LAN.
I have my various windows machines (2) and ubuntu machines (2) installed and working, seeing each other across the network but not allowing me any access.

for instance, from my Ubuntu laptop looking up the network, I am being blocked by a "failed to retrieve share list" error.
Or, if I click through to the windows machines, I see the machines behind the workgroups but then Nothing for shared folders (of which I know there are some)

I "think" I have Samba and shares set up correctly.
I have tried too to follow various Samba How To guides but they are pretty strange.
I hope you can help.

Peter

---

