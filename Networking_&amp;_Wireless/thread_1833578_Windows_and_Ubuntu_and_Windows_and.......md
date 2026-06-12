---
title: "Windows and Ubuntu and Windows and......"
date: 2011-08-26
forum: Networking &amp; Wireless
---

### Post by ubudunce on 2011-08-26
Hi folks
I am a complete noob to this Ubuntu stuff, so please forgive me if I ask a dumb Question, or ramble on....
I have been told that I am trying to run before I can crawl, but here goes.....

I have a few old Windows programs that are no longer supported or run correctly on Vista or Win7, but work happily in XP. These are used for my business and are mission critical. The two main ones are Labels Unlimited and Sage Line50 ver11. I am fed up with being told to keep buying new software because Windows no longer supports my software. LU2 is no longer available, So I have been persuaded to try Ubuntu.

So far so good.
Here's the snag - both programs access their data across the Windows Domain, and need to see a mapped drive (G: )!

I have installed Ubuntu and Wine(1.2)and Samba. I have (after a bit of faffing around) installed both software packages on the Ubuntu computer. They both seem to work fine with local data. I can see (and mount) the windows data share (server1/data), however I cannot seem to find out how to assign a drive letter to it. I realise that Linux doesnt use drive letters in the same way and have been told that Samba is the way to do it, but it seems that Samba is fine for sharing Linux folders, but not what I need.
Bearing in mind that I am a complete novice with Ubuntu (cant even find the Terminal window!!), have only been trying it (Ubuntu) for 4 days, and my programming skills stopped at 6502 assy language and paper tape Basic. Can anyone talk this dunce throw the operations, or is there a "Dummies Guide"? I have spent a day and a bit browsing the Interweb thingy and have found lots of stuff about accessing Windows shares, but nothing in particular showing how I can assign a drive letter to a Windows share, so that I can run Windows software under Ubuntu.
I realise that this may be an unusual way of running things, but surely I cant be the only one?

Help ](*,)

---

### Post by tommpogg on 2011-08-26
> **ubudunce said:**
> 
 I have spent a day and a bit browsing the Interweb thingy and have found lots of stuff about accessing Windows shares, but nothing in particular showing how I can assign a drive letter to a Windows share, so that I can run Windows software under Ubuntu.
 

I'm quite sure that this is an imposible task. Linux and Windows filesystems are completely different: in Linux you don't have any letter labelling a partition; all partitions are connected through the root partition (/).
Anyway there could be some workaround that I don't know.

If you are interested you can find additional information on Linux filesystem in textbooks (for instance, in [this one]("http://tldp.org/LDP/intro-linux/html/")).

PS: in Ubuntu you can open a terminal by clicking Applications -> Accessories -> Terminal

---

### Post by ubudunce on 2011-08-26
Thanks for your quick reply. I hope that isnt true as it means that Linux is out of the question as a business OS, from my point of view :(:popcorn:

ta for terminal link :D

---

### Post by tommpogg on 2011-08-26
Have you looked for Open Source alternatives for Labels Unlimited and Sage Line50 ver11?
What are they used for?

You can try to open a thread on this forum to ask for alternatives.

I also use the PC for my job and I know that is very hard to run (some) professional software on linux.

---

### Post by debd on 2011-08-26
Am not sure if I understand your problem, but if you just want to map partitions to drive letters in wine, for ease of use with windows apps, you can do so by:

mount the drive, open Wine > Configure wine, under the drives tab select 
'add' , select the drive letter; 
now click on the browse button beside the path field and point to /media/<your drive>

---

### Post by Scunizi on 2011-08-26
debd has it right.. it should be that easy.. a replacement for your labeling program might be glabels.  Very flexible, templates for Avary, customize your own templates, add graphics, data merge etc.. it looks simple and is but powerful.

---

### Post by ubudunce on 2011-08-26
> **debd said:**
> Am not sure if I understand your problem, but if you just want to map partitions to drive letters in wine, for ease of use with windows apps, you can do so by:

mount the drive, open Wine > Configure wine, under the drives tab select 
'add' , select the drive letter; 
now click on the browse button beside the path field and point to /media/<your drive>



Hmmm that doesnt work for me... I have the mounted drive on my desktop ( I know its mounted coz it gives the option to unmount it ;)) but when I configure Wine/drives - under media it only says "floppy" and "cdrom". is this finger trouble?

I dont want to look for alternative software for, amongst other reasons, there are over 4000 labels set up that I dont want to re-generate.

did i explain the drive I want to map is shared from a windows server?

---

### Post by Rhizoid on 2011-08-27
> **ubudunce said:**
> Hmmm that doesnt work for me... I have the mounted drive on my desktop ( I know its mounted coz it gives the option to unmount it ;)) but when I configure Wine/drives - under media it only says "floppy" and "cdrom". is this finger trouble?

I dont want to look for alternative software for, amongst other reasons, there are over 4000 labels set up that I dont want to re-generate.

did i explain the drive I want to map is shared from a windows server?

Ok - to use Winecfg.exe to map a drive to a windows share persistently, mount the windows share as part of the file system, not by browsing to it.  It's also easier with sharenames which are a single word - i.e. no spaces in the name.  To do this...

Open a terminal (Applications --> Accessories --> Terminal )

Copy and paste this code into the terminal:

```
sudo apt-get update
sudo apt-get install smbfs
```It will ask for a password, this is your normal login password for Ubuntu.  It will print some text to the screen and ask if you're sure you want to continue (Y/n), press Y and press return.

Now make a suitable mount point for the windows share - I'd suggest using a subfolder of the /mnt directory... it's what it's for.

```
sudo mkdir /mnt/winshare #replace the word 'winshare' with a foldername of your choice
```To test you can mount your windows share modify the following code, replacing everything in curly brackets ( { } ) with your own information:

```
sudo mount -t cifs -o username={windows server/domain userid},uid=1000,gid=1000 //{windows server IP address}/{windows server sharename} /mnt/winshare #replace winshare with the foldername as above
```To check the share is mounted correctly:

```
mount
```The last line of the output from the above command will look something like:

//192.168.1.1/winshare on /mnt/winshare type cifs... etc

Now start winecfg (Applications --> Wine --> Configure Wine) or ```
wine winecfg.exe 
```Click the Drives tab, click the Add... button and note the next available drive letter and click OK.  Change the Path: statement to /mnt/winshare (change winshare as above), click Apply and then OK.

Now run your windows/DOS app and check you can use the Windows share as the drive letter you just assigned.

If all is well you need to modify the /etc/fstab file to automatically mount the Windows share on each reboot to make the changes made above persistent - let me know if you need a walkthrough for that part.

Cheese!

---

### Post by northd_tech on 2011-08-27
> **ubudunce said:**
> 
I have a few old Windows programs that are no longer supported or run correctly on Vista or Win7, but work happily in XP. These are used for my business and are mission critical. 
I've got the same situation with some old lab, data acquisition, and 'heirloom' family records that simply will NOT run on anything newer than Win98 & XP.

Have you considered running 'virtual machines' under Vista/Win 7?  That might be easier than Wine (which has its own sizable collection of issues, but it is getting better slowly).

VMWare is probably the best that I've used (and I think the VMWare Player is available after a free registration process):
[http://www.vmware.com/products/player/](http://www.vmware.com/products/player/)

Free PC / Intel i86 Emulators and Virtual Machines
[http://www.thefreecountry.com/emulators/pc.shtml](http://www.thefreecountry.com/emulators/pc.shtml)

Under Win7 there is also "XP mode":
[http://www.microsoft.com/windows/virtual-pc/](http://www.microsoft.com/windows/virtual-pc/)

Running older software on newer OS'es, you will likely run into "Missing DLL" errors:
[http://www.dll-files.com/](http://www.dll-files.com/)

or messages about the Visual Basic or Visual C runtimes missing:
[http://www.snapfiles.com/help/missingfiles.html](http://www.snapfiles.com/help/missingfiles.html)

I'm still looking for a workaround to the old M$ Access 97[-ish] Jet database obsolescence and 64-bit incompatibility for a few of my important programs...

Vb6 / Microsoft Jet Database And 64-Bit Windows Vista
[http://thedailyreviewer.com/dotnet/view/vb6-microsoft-jet-database-and-64-bit-windows-vista-101696565](http://thedailyreviewer.com/dotnet/view/vb6-microsoft-jet-database-and-64-bit-windows-vista-101696565)

Jet 4.0 Database hotfix
[http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6053](http://www.microsoft.com/download/en/details.aspx?displaylang=en&id=6053)
[http://support.microsoft.com/kb/239114](http://support.microsoft.com/kb/239114)

Microsoft Jet Database Engine
[http://en.wikipedia.org/wiki/Microsoft_Jet_Database_Engine](http://en.wikipedia.org/wiki/Microsoft_Jet_Database_Engine)

Good luck either way.

EDIT:  You might have some luck with QEMU (which might already be installed on your Ubuntu system, or the newer Virtual Bricks front end):
[http://virtualbricks.eu/](http://virtualbricks.eu/)

[http://en.wikipedia.org/wiki/Qemu](http://en.wikipedia.org/wiki/Qemu)

or Virtual Box:
[http://www.virtualbox.org/](http://www.virtualbox.org/)

You might need some Win95/98/2000/NT/XP CD's to set up the virtual machine though.

---

### Post by ubudunce on 2011-08-27
Wow - a Dummies guide :D

Thanks for that (and the phone call) It now appears sorted and I can at least test the software next week :D

---

