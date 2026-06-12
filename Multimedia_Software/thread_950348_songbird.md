---
title: "songbird"
date: 2008-10-17
forum: Multimedia Software
---

### Post by acegik on 2008-10-17
hi ive just downloaded the recet songbird from songbird.com, nce i downloaded the program i extracted the file and i double click in a file callsongbirdand t open songbird. my question is, it didnt ask me to installanything so im i basicly able to run songbird in ubuntu wthout installing it? if so is it any different rom installing it to ubuntu? do  get to use all the featurs without installng it?or when i cliked in the file did i installed into my computer if so w can i remove it?

thanx for the elp

---

### Post by kpkeerthi on 2008-10-17
> 
so im i basicly able to run songbird in ubuntu wthout installing it? 

Yes. 

> 
if so is it any different rom installing it to ubuntu? 

You just extracted the archive to a folder. You would use a deb-packaged-songbird (.deb file) if you want to 'install' in Ubuntu. If you installed it from a deb file, the files would have landed to a different location. Actually, installation in Linux is usually nothing more than automated copy of files from the package to designated destinations.

> 
do get to use all the featurs without installng it?

Yes.

> 
 when i cliked in the file did i installed into my computer if so w can i remove it?

No. Just delete the folder where you extracted the file and you are good to go.
If you installed it from a deb file you would use apt/aptitude/apt-get/synaptic (the package managers) to uninstall songbird.

---

### Post by acegik on 2008-10-17
so is there ny difference on a installed songbird and one without installing it? do i get all the features without installing it? im i able to use all the pluguins or downloaded content? also the reason im thinking of using songbird is for my ipod, is it compible with a ipod touch 16gb?

---

### Post by Paul41 on 2008-10-17
I haven't heard of anyone being able to get a Touch to work with anything except iTunes.

---

### Post by Dirty Ole on 2008-10-17
In case you are interested in installing Songbird, go [here]("http://www.getdeb.net/search.php?keywords=songbird").

---

### Post by Paul41 on 2008-10-17
> **acegik said:**
> so is there ny difference on a installed songbird and one without installing it? do i get all the features without installing it?

Everything will be the same with songbird either way.

---

### Post by acegik on 2008-10-17
so i shouldnt intall it i sould use without intalling it?so i guess im just gona use it without istalling it

so does anyone knows a program toput music to my ipod touch or a program to find the mssing info iy music and the album art?

---

### Post by acegik on 2008-10-17
sorry i have another question, where aare all the pluguins that im gona download like feathers for songbird, where are they going to save?

---

### Post by AlanR8 on 2008-10-17
> I haven't heard of anyone being able to get a Touch to work with anything except iTunes.

I have.

There are various howto files that explain how to get a Touch to talk to Amarok (KDE music player). To save you some time, here's the howto I followed and respect to the original poster, sorry, name not included:

> The following guide allows you to wirelessly sync an iPhone with Amarok in Ubuntu 7.10, including adding, editing and playing songs and playlists. 
Note :- it requires a jailbroken iPhone.
Step1 :- Set up the iPhone
On your iPhone:
Click Settings &#8594; General and set Auto-lock to Never. This will ensure the iPhone keeps the WiFi connection open.
Click Settings &#8594; WiFi and select your WiFi network. Click the Static button and change the IP Address to something outside the dynamically assigned range of your network. For example, if your wireless router normally assigns 192.168.1.1 - 192.168.1.5, try 192.168.1.10. This will ensure your iPhone is always contactable at the same address for syncing.
Open Installer.
Click on All Packages &#8594; OpenSSH &#8594; Install.
Click All Packages &#8594; BSD Subsystem &#8594; Install
Step2 :- Set up Ubuntu
A third party source provides the ipod convenience package needed to properly mount and unmount an iPhone or iPod Touch, and for gtkpod users, a newer gtkpod that’s required for the iPhone and iPod Touch.
First you need to edit the /etc/apt/sources.list file
sudo gedit /etc/apt/sources.list
add the following line
deb [http://ppa.launchpad.net/ipod-touch/ubuntu](http://ppa.launchpad.net/ipod-touch/ubuntu) gutsy main
Save and exit the file
Update the source list
sudo aptitude update
Install the ipod-convenience and amarok packages
sudo aptitude install ipod-convenience amarok
When asked, enter the IP address of your iPod Touch or iPhone that you selected earlier. When asked for a folder to mount your iPod Touch or iPhone, either leave the default of /media/ipod or another folder if you prefer - just remember to use that folder name for rest of this guide. The package will make the folder for you.
Step3 :- Set up Amarok
Click Applications &#8594; Sound and Video &#8594; Amarok
When you first open up Amarok:
Click Settings &#8594; Configure Amarok.
Choose Media Devices.
Hit Add Device.
Select Apple iPod Media Device for the plugin type.
Point it at your mount point, /media/ipod.
Back in the main app, click the blue cog icon called Configure Device just above the iPhone or iPod Touch. For Pre-Connect Command, add iphone-mount, for the Post-Disconnect Command, add iphone-umount
Click Connect. After entering your password, your iPhone or iPod touch should now appear in Amarok.
You can now add, edit, and delete music to the iPhone like any other device. Just drag the music files into Amarok, and hit Transfer to move them to your iPhone. When you’re done, stop any music playing from the iPhone and click Disconnect.
Music should show now up in the iPhone immediately.
Note: If music doesn’t show up immediately this may be due to a bug recent BSD Subsystem packages missing the killall command. If so, you can download killall for iPhone, move the ‘killall’ file to /usr/bin/on your iPhone, and enable the execute permission.



---

### Post by 1jackjack on 2008-11-01
> If you installed it from a deb file you would use apt/aptitude/apt-get/synaptic (the package managers) to uninstall songbird.

Slightly off-topic, but I installed songbird from a .deb, and it's not showing up in synaptic. I'm sure I could use apt-get to remove it, but any ideas why it wouldn't be showing up in synaptic???

Cheers

---

