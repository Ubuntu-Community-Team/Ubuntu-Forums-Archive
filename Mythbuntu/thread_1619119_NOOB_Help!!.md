---
title: "NOOB Help!!"
date: 2010-11-11
forum: Mythbuntu
---

### Post by clgshaft on 2010-11-11
Hey Guys,

New here, and new to linux and mythbuntu. I have been reading quite a bit, and have acually learned quite a bit. I am trying to get mythbuntu working on an old PC prior to investing in a new build, and for the most part so far I am pleased.

I am wanting to use netflix and hulu, and have installed the required files, but I am having problems adding the links to mythtv mainmenu.

these are the instructions I am following.

** MythFrontend Customizations**

 The next step allows you to launch Hulu from your Mythfrontend.   We're going to edit the XML files for your theme for this.  Copying XML  files from /usr/share/mythtv into ~/.mythtv allows you to customize  menus and prevents them from being overwritten during an upgrade.   
Get a command line, and enter the following: 
 cp /usr/share/mythtv/themes/defaultmenu/mainmenu.xml ~/.mythtv
*# (or library.xml or wherever else you want to put the hulu command)*
This assumes you haven't already edited your Mythfrontend's  appearance.  If you have, edit your existing copy of mainmenu.xml.  In  my case, I wanted Hulu available on the main menu.  You can add it to  wherever you like, you just need to copy the right XML file and edit it. 
Now, open up mainmenu.xml (or whatever file you copied over) in  your favorite editor.  Add the following lines where you want your Hulu  button to live. 
 <button>
       <text>Hulu Desktop</text>
       <action>EXEC /usr/bin/huludesktop</action>
</button>
The next time you run your Mythfrontend, the button will appear on your main menu. 



The problem is that I cannot create this .mythtv folder under /home/username to copy the main folder file too. i am copying the script to terminal and it does not work. I tried to create a folder called .mythtv and that didnt work either. is the "." important? what am i doing wrong?


thanks 

 ** **

---

### Post by itlarson on 2010-11-11
Two things you may not be aware of if you are new to Linux:

1. The leading "." makes the directory hidden.  You may be creating it, and not seeing it.  Choose "show hidden files" from the menu of your file manager, or use "ls -a".

2. There is no Linux Netflix client.  Email them and complain.

---

### Post by clgshaft on 2010-11-11
you are correct. the file folder was there, i think like in three different places. On mythbuntu menu on watch tv worked, the rest could not find the xml file.

what is the proper way to do this? do I need to copy all the folders to .mythtv? where in the mainmenu xml do I want to add the button for hulu?

I have more questions, but just want to solve one think at a time.


thanks

---

### Post by clgshaft on 2010-11-12
I am trying to mount my nas using:
sudo mount -t smbfs -o username=xxx,password=xxx "//192.168.1.102/public" /mnt/nas1

getting:
Couldn't chdir to /mnt/nas1: No such file or directory


how do i get working?

---

### Post by elgordo123 on 2010-11-12
Did you first do make the directory?

sudo mkdir /mnt/nas1  

then run your mount command.

---

### Post by clgshaft on 2010-11-12
perfect, that worked.

how to i mount so it is always mounted after reboot?

thanks

---

### Post by ahood on 2010-11-13
> **clgshaft said:**
> perfect, that worked.

how to i mount so it is always mounted after reboot?

thanks

Edit fstab

> 
sudo nano /etc/fstab

In a new line enter

> 
//192.168.0.102/public /mnt/nas1 smbfs rw,auto,user,username=xxx,password=xxx 0 0


Replace rw with r to make shared folder read-only.

Also see [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

I hope this helps.

---

### Post by nickrout on 2010-11-14
> **ahood said:**
> Edit fstab



In a new line enter



Replace rw with r to make shared folder read-only.

Also see [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

I hope this helps.


NO, do NOT put the password in fstab. The whole world can read fstab. instead use cifscredentials=/root/passwordfile and put the credentials in /root/passwordfile, and make that readable ONLY by the root user.

---

### Post by clgshaft on 2010-11-14
> **ahood said:**
> Edit fstab



In a new line enter



Replace rw with r to make shared folder read-only.

Also see [http://www.tuxfiles.org/linuxhelp/fstab.html](http://www.tuxfiles.org/linuxhelp/fstab.html)

I hope this helps.


this did not work. at the bottom of fstab i entered that command, and saved, and it doesnt auto mount on reboot. I have tried with and without # in front of the command.

thanks

---

