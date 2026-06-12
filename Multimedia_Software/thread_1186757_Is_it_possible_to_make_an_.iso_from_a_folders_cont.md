---
title: "Is it possible to make an .iso from a folders contents?"
date: 2009-06-13
forum: Multimedia Software
---

### Post by StarWarsSDI on 2009-06-13
Hello i'm fairly new to linux but having fun learning new horizons I have downloaded Rosetta Stone software which runs on windows. I have wine up and running but im having problems creating a .iso from a folder. the files are for the software.

these are the instructions:

Instructions: Download everything included, unzip, and put everything in the same folder. Then burn that folder's contents (but not the folder itself) to 1 DVD. Install RosettaStone from the Application folder and then run program. (DVD is needed to run, unless you make and mount an ISO image. See: Extras/ISO Tools/Readme.txt) 


Also note, I had to create an ISO file (with Magic ISO) before burning since Nero 7.0 choked when trying to cache all of the folders.


i have mounted the folder that I need to turn into an .iso but I can't find out how to do it. :( I know how to convert a .avi and .mpeg4 files to .iso but how do you convert a folder to a .iso the instruction say he used Magic ISO but that isn't avaliable for linux is there another program that I can use, I already have K3b, brasero, devede, and dvd disaster none of those programs complete this task. Any help would be greatly appreciative Thanks..... :D

---

### Post by ad_267 on 2009-06-13
Umm Brasero can do this easily. Just add all the folder contents to a data dvd project, click on burn, and write to an image file.

---

### Post by StarWarsSDI on 2009-06-13
> **ad_267 said:**
> Umm Brasero can do this easily. Just add all the folder contents to a data dvd project, click on burn, and write to an image file.

I need to make it into a .iso file before I burn it though the file is 4.4 gb and it will stop like halfway through is there a program i can use that's equivalent to Windows Magic ISO, or Power ISO

---

### Post by ad_267 on 2009-06-13
What's the point in making an iso file before you burn it? You either want to make an iso file so you can mount the disc image without having to burn it to disc, or you can just burn the files directly to disc.

If you want to make an iso image from files then Brasero can do this. If Brasero is having issues then k3b can. There's no need to use Windows software through wine just to create an iso image.

---

### Post by StarWarsSDI on 2009-06-13
> **ad_267 said:**
> What's the point in making an iso file before you burn it? You either want to make an iso file so you can mount the disc image without having to burn it to disc, or you can just burn the files directly to disc.

If you want to make an iso image from files then Brasero can do this. If Brasero is having issues then k3b can. There's no need to use Windows software through wine just to create an iso image.

Thanks I have it now I used brasero like you recommended I don't know why I thought I had to make an .iso before I burned it the uploaders directions said that the file was to big and it froze nero so i figured that it had to be a .iso first but any how I got it to work thanks to you I appreciate it very much.......now I can learn new languages:D

---

### Post by StarWarsSDI on 2009-06-13
I just burned it to a dvd and its working fine but if I wanted to do like you said and make a .iso and mount it first what are the steps to do this seeing as I haven't before never made a .iso from files and the options under k3b or brasero only say write image to cd or dvd if it's not in .iso form already how do you do it?

---

### Post by ad_267 on 2009-06-13
When you burn the disc from brasero there's a drop down menu where you select the disc to burn to. You should be able to select "Image File: something.iso"

---

### Post by Scotty Bones on 2009-06-14
> 
Instructions: ..snip..(DVD is needed to run, [COLOR="Red"]unless you make and mount an ISO image[/COLOR]. See: Extras/ISO Tools/Readme.txt)


You can mount the iso when needed, instead of having to carry around a DVD with you when ever you need the program.  I use _gmountiso_. It can be found in the repos.

---

### Post by andrew.46 on 2009-06-14
Hi StarWardSDI,

> **StarWarsSDI said:**
> [...] but if I wanted to do like you said and make a .iso and mount it first what are the steps to do this seeing as I haven't before never made a .iso from files and the options under k3b or brasero only say write image to cd or dvd if it's not in .iso form already how do you do it?

If you wanted to move past the glitz of the gui burners you can *easily *create an iso from the command line. First change to the directory that is holding all of your files and then:

```
mkisofs -v -dvd-video -o ../output.iso .
```

and this will create the iso in the directory *above* your files. 

Andrew

---

### Post by christophevr on 2009-10-15
> **StarWarsSDI said:**
> I just burned it to a dvd and its working fine but if I wanted to do like you said and make a .iso and mount it first what are the steps to do this seeing as I haven't before never made a .iso from files and the options under k3b or brasero only say write image to cd or dvd if it's not in .iso form already how do you do it?

Hello there are many way's to mount an iso image. But her I just made a small script to mount and unmount an iso from out the nautilus browser

when you extract this file and copy the mountiso.sh and unmountiso.sh to .gnome2/nautilus-scripts folder. You will be able to mount an iso by clicking right mouse bouton and sripts command. mountiso or unmountiso

it's about the same like the Gnome-iso but if find  faster and use this now already for many years (before i worked with debian) 

it's tested in jaunty as well since I just started using ubuntu

greetings christophe

I just changed the scripts and now i'm usinf fuseiso into in it.
So you will not have to log in as sudo anymore.But first install the fuse packages they are on de ubuntu reporsites at least in jaunty well.

just read the isomountreadme.txt file

greetings and again easier

---

### Post by christophevr on 2009-10-17
Hello again

Here again extra adaptation.

First I added a check so that it will only mount files
with .iso .ISO .nrg .NRG extention

Also I added the set -e parameter to instantely exit the script if an error occurss this to avoid not wanted mounts, But especially in the unmount command an not wanted removing of map will not occur anymore. It was possible before whit an empty map where an 1 was in front of it

greetings enjoy

---

### Post by christophevr on 2009-10-17
[SIZE="6"][B]FORGOT ONE IMPORTANT THING after you installed all the fuse programs  You must become a member of the fuse group as well otherwise it wil not work but just make an empty map 
how ?
in terminal type sudo useradd -G fuse yourusername:):[/B][/SIZE]H

---

