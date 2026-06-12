---
title: "SpeedTouch 330 USB DSL help pleez??"
date: 2006-02-12
forum: Networking &amp; Wireless
---

### Post by Esskie on 2006-02-12
Hi There, 
I've been playing around with the Live Ubuntu 5.10 "Breezy Badger" CD release as I'm not too knowledgable about linux I'm not sure how to go about setting up my modem, it's recognised in Device manager and I've tried various settings but nomatter what I do, I just can't get a connection.
 
I have Mandriva 2006 here which I was/may still install? but I really like what I've seen of Ubuntu so far and think I could settle into using it without much trouble, however I need my net access.
 
Firstly, can anyone say if they have a Speedtouch 330 USB modem working with this distro or is it a case of it maybe not being supported?. I'm so content with what I've seen so far that I even thought about installing a 56k just to get net access with it!!.
 
I could be way off here? but it seems to be that due to me not entering a dial up number, the 'ok/next' button stays greyed out?.
 
Ideally, if I could setup a dual boot Mandriva/Ubuntu system?, I think it'd be all I need to ditch win for good?.
 
Any help would be greatly appreciated.
 
Meantime, I'm going to have my head stuck into the How To's etc & see if I can find anything?. Btw, my mouse is an optical USB scroll mouse & it's working fine.
 
Regards, Esskie.

---

### Post by Nyati on 2006-02-12
Hi

Can I suggest you install Ubuntu Breezy Badger 5.10 before you try and install your SpeedTouch Usb Modem. Before you install the distro, make sure you have everything you need for the modem installation attachment. I'd hate for you to lose your internet connection before getting anywhere. It's always best to have 2 computers with an internet connection and a usb memory stick to transfer things if you need to.

During install you will be asked to configure your ethernet connection. Don't do this unless you have an ethernet connection. I cannot support this but may be able to help.

Once ubuntu is installed, follow the HowTo that I have compiled. It is configured for the SpeedTouch 330 USB modem.

I have completed the HowTo many times because of computers crashing etc. I just had to do it the hard way...searching and fighting with instructions that were confusing or didn't explain enough.

Anyway, copy the attachment and/or print it. If you have any problems, I could possibly help. This HowTo I compiled makes sense to me and is pretty straight forward. I hope it works for you!

---

### Post by Esskie on 2006-02-12
Hi there,
I just typed a relatively long reply only to have it fail when I hit reply!!.
 
Thanx for the reply my friend, my aplz if this reply may seem a tad short but I don't want to type another reply only to have it fail again! :rolleyes: .
 
The how to you sent me is printed out as I only have access to 1 PC atm due to new heating system being installed in my house.
 
The Live version was to see what Ubuntu was like before I installed it I suppose?, it was Mandriva 2006 I've been planning to install until yesterday when I saw Ubuntu & decided to check it out.
 
I've downloaded the new firmware for the 330 from [here]("http://www.linux-usb.org/SpeedTouch/mandrake/index.html") and have firmware v.KQD6_3.012 ready to install as I was prompted for it while halfway through installing Mandriva 2006 from the DVD I downloaded. After your reply I found a script called speedtouch-adsl.sh which came from [here]("http://www.linux-usb.org/SpeedTouch/mandrake/index.html") along with info on installing the 330 on MDK.
As mine isn't the silver 330 it's KQD6_3.012 I have to use yes?.
 
You wouldn't think I've been 'playing' with MDK since v7.2 would you!!. I actually configured 9.2 to work with a 56k dial up modem but didn't stay with it due to having no joy with getting my NVidia gfx card to work, a problem I am going to have to overcome again.
 
This time though I plan on sticking with it & seeing it through to the end as I would ideally like to move to linux totally and not use Win!, I have XP Pro on this PC too.
Thee is an 80Gb HD which I'm thinking about maiking a 10Gb partition on for a linux distro, also I have an old 6.4Gb HD in this system which is where it will probably end up as I believe 6.4Gb to be plenty big enough for a linux install with lots of room to spare?.
 
It's an AMD64 3200+ with 512Mb of DDR400 memory so maybe a swap file of approx 100Mb??.
 
Btw Nyati, I've read about people using Partition Magic to partition & install linux with??, how is this done?, I have only ever used it to make partitions for use with Windows. This is supposed to be able to setup your swap file and everything??, I have a feeling though it may be better to let linux take care of it itself?.
 
Also, in networking in Ubuntu there are modem, & TTY-0 through to TTY-3 or 4 listed? in networking setup, which should I choose please?.
 
I got half way through installing MDK 2006 Free until I was prompted for the new firmware for the 330 so I have those here.
 
Also the 'Next/OK' button is greyed out until I enter a phone number to dial up but I'm using 2Mb DSL & have no dial up number??.
 
I'm sorry about this post being short & perhaps not so much info, if you need anymore info I'll be glad to give it to you.
 
You mentioned a book, I'm afraid all I have is an old book called [COLOR=red]Linux in easy steps [/COLOR][COLOR=black]by David Nash. It's okay as it covers the basics through to the more complicated stuff but it is getting a bit old now.[/COLOR]
 
If I can get the modem working and then my NVidia gfx card I would like to move to linux 100% and not have to use windoze at all!, the problem being I need net access and my two boys enjoy online gaming, infact I still like the occasional blast on Quake etc even now! :twisted: (I'm just a big kid at heart :rolleyes:  .
 
If you need anymore info that I have left out? just ask & I'll be glad to give it to you, likewise, I shall post back here after I have read the How Tos you have been so good as to write & link for me, many thanks!.
 
Btw, what do you think about the speedtouch-adsl.sh script [here]("http://christophe.delord.free.fr/en/adsl/debian.html") ?, it mentioned the installation must be done by the **root** user or a '**sudoer**' user: 
    $ /mnt/floppy/speedtouch-adsl.sh  # If the script is on the floppy diskBest Regards Esskie.

---

### Post by Nyati on 2006-02-12
Hi

As mine isn't the silver 330 it's KQD6_3.012 I have to use yes?.

Answer: If your modem is an Alcatel or Thomson and it is a Version 4 modem, I don't think it matters what colour it is.

Btw Nyati, I've read about people using Partition Magic to partition & install linux with??, how is this done?

Answer: I've never used partition magic, but I wish I had it about 3 days ago. 
When I installed Linux on my Laptop IBM T30 I already had XP Pro on it. The windows filesystem was NTFS which was great for adding Linux to it. Unfortunately, 3 days ago I decided to remove the linux partition and reclaim it for windows as I've got another box IBM X30 that I wanted to load linux onto. Anyway, IBM T30 crashed, I deleted the Linux partition and the swap partition, but this doesn't happen and when you reboot, the grub installer appears and windows is inaccessible. So I reinstalled Linux on T30 and have Win XP on X30.

Partition Magic would have worked, I reckon.

---

### Post by ssam on 2006-02-12
i need to do this for a friend. i found some instructions [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html](http://www.linux-usb.org/SpeedTouch/ubuntu/index.html) but have not tested them yet.

---

### Post by Nyati on 2006-02-12
I tried those instructions, but they didn't work for me, that's why I compiled my own method, which is basically rewritten with more detail.

I've attached it here for you.

---

### Post by Esskie on 2006-02-12
Nyati my friend,
I have a catch-22 situation here!, I saved the instructions you gave me beside the 330 firmware on my second HD which is still FAT32 (my main HD is NTFS) but I can't 'see' my windows drive or my FAT32 drive while I'm running linux??.
 
I can 'see' & access my optical drives (DVD & CD burners), my floppy too but cannot access it, I was very cautios while logged in as root & didn't want to do too much messing around incase I caused some serious damage.
 
PS: do you need/want P/Magic v8.0?

---

### Post by Nyati on 2006-02-12
Esskie

I can't 'see' my windows drive or my FAT32 drive while I'm running linux??.

Have you checked to see if the partition is in the file manager?

You might want to try this, [http://www.ubuntuguide.org/#automountntfs](http://www.ubuntuguide.org/#automountntfs)

---

### Post by rob2nd9th on 2006-02-13
Hi I use a Speedtouch 330 usb modem on ubuntu (brezzy) on problem - I have a script on disk that sets it up for you would that help?

---

### Post by Esskie on 2006-02-13
Hi There,
My aplz for not replying last again Nyati, I ended up making a mess of the partitioning during the install so put the small 6.4gig drive back the way it was with P/Magic so I could start again today.
 
I have the speedtouch-firmware_0.3012k_all.deb file, although I already have the firmware it's not packaged as a debian *.deb file so I thought it best to just get the deb file in order to make the info you gave me easier to follow through.
 
I don't know what happened with the partitioning??, I 'gave' the install all of the 6.4gig but ended up with an error message informing me that there wasn't enough room to install?.
I encountered this with MDK too, I think I'm allocating too much space to the wrong things? ie;too big a swap, either too big? or too small '/' partition etc,?.
 
Today I plan to start again from scratch but try to get it right this time!.
 
rob2nd9th** - **Thanx for the offer, as you may see Nyati has posted a script which, I think?, does the same?. If you'd like to post it anyway though it certainly wouldn't hurt.
Can you do as Nyati did & post it as a link that I can save/rename etc,?.
 
Also, I have to say, having only tried Mandrake/Mandriva linux (and liked it), I think from first impressions that I'm going to like Ubuntu as much if not more?.
 
I've read it's possible to have multiple distros use the same partitions?, if this is so? then I may eventually try & have Ubuntu and MDK both on the same system?.
 
Oh, one last thing, in the script Nyati it mentions unplugging the usb modem before executing the script.
Should I unplug it after I've installed Ubuntu so it knows it's there or only before I run the script?.
 
One last thing, thanks for being so very patient with me, I admit I **should have** done more reading before diving in & trying stuff out. I refer to the [http://www.linuxhelp.net/newbies/]("http://www.linuxhelp.net/newbies/") pages & other guides.
 
Regards, Esskie.

---

### Post by Esskie on 2006-02-13
I forgot to mention,
As I have Partition Magic here, is it easier or am I perhaps better to setup (the partitions) and/or install linux using that first?.
 
The only problem I can forsee with that though is, what happens when you come to that part of the actual linux installation process?.
 
Regards, Esskie.

---

### Post by Nyati on 2006-02-13
Hi Esskie

Q - I don't know what happened with the partitioning??, I 'gave' the install all of the 6.4gig but ended up with an error message informing me that there wasn't enough room to install?.
I encountered this with MDK too, I think I'm allocating too much space to the wrong things? ie;too big a swap, either too big? or too small '/' partition etc,?.

Answer - You can verify the amount of swap space available on your system using: 
cat /proc/meminfo
The general recommendation is that you should have: at least 64 MB of total (physical+swap) memory for a system running X-windows, and swap space at least 1.5 times the amount of the physical memory on the system. 
If this is too complicated, you might want to have a swap twice as large as your physical (silicon) memory, but not less than 64 MB. 
If you ever need to change your swap, here are some basics.

Swap partitions
You can have several swap partitions.
Create the partition of the proper size using fdisk (partition type 82, "Linux swap") or you can use partition magic.
Format the partition checking for bad blocks, for example: 
mkswap -c /dev/hda4 
You have to substitute /dev/hda4 with your partition name. Since I did not specify the partition size, it will be automatically detected. 
- Enable the swap, for example: 
swapon /dev/hda4 
To have the swap enabled automatically at bootup, you have to include the appropriate entry into the file /etc/fstab, for example: 
/dev/hda4 swap swap defaults 0 0 
If you ever need to disable the swap, you can do it with (as root): 
swapoff /dev/hda4.

Q - I've read it's possible to have multiple distros use the same partitions?, if this is so? then I may eventually try & have Ubuntu and MDK both on the same system?.

Answer - It would be more economical on your hard drive to create seperate partitions. By doing this, you wouldn't have any conflicts between the different distibutions. I've never heard of having 2 distro's running on the same partition. If you want to partition your hard drive, a reasonably logical way to do this would be to divide your entire 40 GB hard disk into three primary partitions and one extended partition and the extended partition is further divided into two logical partitions.
I have attached a diagram for you to get a better idea.

Q - Oh, one last thing, in the script Nyati it mentions unplugging the usb modem before executing the script.
Should I unplug it after I've installed Ubuntu so it knows it's there or only before I run the script?.

Answer - First you should install Ubuntu, you do not need to have your modem plugged in, I didn't. Remember, when you get asked about your ethernet connection, I ignored this, as I don't have an ethernet connection. Once Ubuntu is installed, you can go right ahead with the script. Just remember to have all the requirement first before you leave your connection.

---

### Post by Esskie on 2006-02-13
Hi There my friend,
How are you today?, all is well with you & your's I hope.
 
Before I forget, regarding the multiple distros using the same partition/s. I can't remember (or understand) everything but it was along the lines of them sharing the same /home partition but having separate boot partitions and also when booting the PC, the last distro installed will overwrite Grub or LiLo so a little messing around is required there
>  
you will only be able to boot into the last-installed distro unless you use the boot floppies

 
When I asked if you wanted P/Magic 8.0, I have 2Gb storage space in a GMail Drive (Google). The install files are only 133kb & are only accessable by username & password. I could have stuck it on there for you.
Also, an excellent little partitioning tool I've had for a few years now is Rannish Partitioner, again it's very small at approc 150-160Kb.
 
Ok, What I've done is made a 10Gb partition on my 1st HD as I have had to put the 40gig back into the other system :mad: .
 
This is where Ubuntu (Breezy) is hopefully going to end up, I should have had it installed by now!, don't you just wish there were more hours in the day Nyati?.
 
>  
The general recommendation is that you should have: at least 64 MB of total (physical+swap) memory for a system running X-windows, and swap space at least 1.5 times the amount of the physical memory on the system. 
If this is too complicated, you might want to have a swap twice as large as your physical (silicon) memory, but not less than 64 MB.

Ok, that's what I'd read, a swap approx x1 to x1.5 times the size of the amount of physical RAM installed. Theres 512Mb on this system so a /swap of 500Mb to 750Mb would be adequate yes?.
 
>  
Q - Oh, one last thing, in the script Nyati it mentions unplugging the usb modem before executing the script.
Should I unplug it after I've installed Ubuntu so it knows it's there or only before I run the script?.

Answer - First you should install Ubuntu, you do not need to have your modem plugged in, I didn't. Remember, when you get asked about your ethernet connection, I ignored this, as I don't have an ethernet connection. Once Ubuntu is installed, you can go right ahead with the script. Just remember to have all the requirement first before you leave your connection.

 
Ok I understand, when I mentioned it asking me about my ethernet connection, it actually was asking about my network devices (or words to that effect). I left it plugged in when installing but although it was recognised, as you know, it isn't working.
 
Nyati, in Network Config, as I can't proceed without entering a phone number to dial up (because it's ADSL I presume), should I worry about this or will the script sort this out for me?.
 
One last thing, despite you giving me the link, It took me a little searching to locate/download the libatm1_2.4.1-17_i386.deb but I have it now so that's everything ready to go now I think.
 
I have the following (incuding my gfx card drivers but I'll install those when the time comes):
 
_libatm1_2.4.1-17_i386.deb_
_speedmgmt.tar.gz_ **and **_speedtouch-firmware_0.3012k_all.deb_ (if I need it?, I have the contents as individual, uncompressed files anyway)
_br2684ctl_
_speedtouch-adsl.sh_ <-- the script you gave me.
 
Btw **rob2nd9th**, post your script for me anyway my friend if you don't mind as I'd like to look at it anyway. Who knows, it may be easier for me if it does everything Nyati's one does automatically?.
 
Regards, Esskie.

---

### Post by Esskie on 2006-02-13
Ok heres an update Nyati,
The install of Ubuntu went fine onto the 10Gb partition I made of C: drive, apart from ending up with 2 x swap files at one point lol!, this was due to creating a swap first then auto-allocating the rest of the free space :rolleyes: .
However, I just deleted the partition, chose to make it 'ext3' then auto-allocated the free space which left me with a swap of just over 400Mb and approx 9.5Gb as ext3.
 
I'm now remembering why I never stick with linux though! :confused: , unfortunately I can't access anywhere other than my DVD & CD burners, my floppy (I think?, it wasn't marked with an X anyway).
 
hda1 (win NTFS) & hdb1 (2nd HD:vfat) are not accessable, hdb1 is where I have libatm1_2.4.1-17_i386.deb, speedmgmt.tar.gz andspeedtouch-firmware_0.3012k_all.deb, br2684ctl and speedtouch-adsl.sh stored atm.
 
I tried logging in as root by switching user & choosing root, where upon I was prompted for my root password as normal but hda1 & hdb1 are still marked with a little red box with an X in them when I browse through .../dev.
 
I got to a dialogue where I had the option of formatting or changing the access path to them but all options are greyed out when I go to choose?.
 
This is different to what I can remember of MDK 9.2 as I could browse to my windows directories etc without any problems.
 
Is this a mount issue?, if so I had the option of mounting the floppy etc but nothing else.
 
Btw incase it's relevant?, even while logged on as root, everything was gui's when I expected it to be a command prompt?.
 
It seems the only option immediately open to me atm would be to burn the files onto a CD and copy them over from there but it seems like a long way for a shortcut if you know what I mean?
 
Regards, Esskie.

---

### Post by Nyati on 2006-02-13
Hi Esskie

Q - Is this a mount issue?, if so I had the option of mounting the floppy etc but nothing else.

Answer - This shouldn't be a mount issue, it should be visible on your desktop. You need to look in your file system and ctrl_alt drag it to your desktop.

Q - Btw incase it's relevant?, even while logged on as root, everything was gui's when I expected it to be a command prompt?.

Answer - When in a terminal whether root or not, you should have a white background window (gui). If you want to be in command prompt you need to press  Ctrl_Alt and F1. You can open up more command-prompt terminals by pressing Ctrl_Alt F2 up to F6. To go back to the GUI you need to press Ctrl_Alt F7.

Q - It seems the only option immediately open to me atm would be to burn the files onto a CD and copy them over from there but it seems like a long way for a shortcut if you know what I mean?

Answer - It seems like it is your only option, unless you have a usb memory stick - good luck!

---

### Post by Esskie on 2006-02-14
Hi There,
 
> This shouldn't be a mount issue, it should be visible on your desktop. You need to look in your file system and ctrl_alt drag it to your desktop.

 
Ok, this is probably me just expecting a different screen while logged in as root, eg: MDK has a red b/ground (on mine anyway) while in as root.
So the Ubuntu desktop just stays the same while in as root but with different permissions yes?
 
> When in a terminal whether root or not, you should have a white background window (gui). If you want to be in command prompt you need to press Ctrl_Alt and F1. You can open up more command-prompt terminals by pressing Ctrl_Alt F2 up to F6. To go back to the GUI you need to press Ctrl_Alt F7.
 
Yes that's what I have, a 'window' as it were, with the white b/ground
 
> It seems like it is your only option, unless you have a usb memory stick - good luck!
 
Now that would be handy but unfortunately I don't have one :rolleyes: , I do have a usb 7-1 card reader for my digital camera which holds 256Mb. I wonder if I could use that?. It doesn't necasseraly (<--spelling) have to hold jpegs I don't think.
 
I have a whole bunch of reading to be doing so I'll make this one short but I'll keep you updated on my progress, or not? :-k .
I'm not going to fall into the trap of relying on the knowledge of others to help me out of this!, it's all part of the learning process. Also, once I know how to do it/stuff, I can do it again another time.
 
Regads, Esskie.
 
Thanx for your help Nyati

---

### Post by Nyati on 2006-02-14
Q - Now that would be handy but unfortunately I don't have one  , I do have a usb 7-1 card reader for my digital camera which holds 256Mb. I wonder if I could use that?. It doesn't necasseraly (<--spelling) have to hold jpegs I don't think.

Answer - You're right, if it's an SD card or other type of memory card, you can use it, as long as you can connect to it.

Good Luck and happy reading.

---

