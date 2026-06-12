---
title: "[SOLVED] I cannot burn a cd using CD-R media"
date: 2008-02-03
forum: Multimedia &amp; Video
---

### Post by maxhoward on 2008-02-03
I want to burn some audio CD's and I have tried both Serpentine and Brasero and neither one recognizes my CD-R recordable media when inserted in the DVD-RW drive.  I get a message that says to insert a CD.  It does, however, recognize CD-RW media.  It acts like the DVD burner wont record on a blank CD-R media.  I can find any settings or preferences that deal with this.  I am using Ubuntu 7.10 on a Dell PC.

Can anyone help me?

Thanks.

---

### Post by manimal347 on 2008-02-04
Is this an official "Dellbuntu" machine? If so, has the support offer for your OS lapsed yet?

Also, make sure you have core backends like CDRtools installed. You can get an idea what you want by going over to the Debian packaging site and seeing what programs like Brasero use as dependencies, and also, what they list as "recommended" and "suggested."

---

### Post by cotcot on 2008-02-04
Try k3b also. 
It might be the CD as well. Have you tried another brand ? If it is an old burner and you pop in high speed CD it might refuse as well.

---

### Post by maxhoward on 2008-02-04
My PC is a DELL desktop dual boot with XP and Ubuntu.  It is not a DELLUbuntu.

Brasero does require cdrtools.  My PC does not have cdrtools or cdrkit installed as near as I can tell.  After reading the Wiki on cdrtools I am certain that that is the solution to my problem.

I downloaded cdrkit and now have a folder on my desktop called
   cdrkit-1.1.6.tar.gz 
which I discovered is a tarball. This folder has lots of subfolders and text files including ones called "install" and "makefile".  I looked at these two files and I don't feel confident that I can do what is needed to do a correct and complete install. 

I do have an installed package  called "GDebi package installer".  Should  I use that? or try to follow the "install" instructions?

BTW I am a newbie.

---

### Post by cotcot on 2008-02-07
I do not know how you got brasero.
If you install it with synaptic than the dependencies should be installed automatically. I have no cdrtools or cdrkit installed and just installed brasero to check what you are writing. I al erasing a cd-rw without error messages.

Do in terminal :
```
sudo synaptic
```
Give your pasword and look for brasero in the list. Install it using synaptic. If you see brasero marked as installed, reinstall it.

The .tar.gz file cannot be installed with GDebi package installer. That is only possible with debian packages (.deb extention). Tar.gz files must be installed with 
```
./configure
make 
sudo make install
```

But as you are new to linux and there is no need for it I do not recommend to install tar.gz packages without further reading howtos etc.. .

---

### Post by maxhoward on 2008-02-07
Thanks for your response.  I uninstalled both Brasero and Serpentine and reinstalled them with Synaptic.  But the problem did not go away.  But in the process of doing that I looked at both CD drives (Places > Computer > CD-RW drive >right click > Properties > Permissions)
and discovered that everything was set to "Read only".  So I selected "Read and write" and got the error message "The permissions could not be changed"  So I guess I need to be super user to do that.  I am the only user on this system so that should not be a problem but I can't figure out how to become superuser to make that change from the GUI.

So do I have to do that with the sudo command in terminal mode?  If so, what is the proper command line?

It seems like this could be the cause of the problem. Hopefully.

Thanks in advance.

---

### Post by kalwisti on 2008-02-17
I have a suggestion for what might be a workaround. My problem was very similar to yours; I tried to create an audio CD (on a blank CD-R disc) using Serpentine, Rhythmbox and Brasero. All failed to recognize the media type, or told me to insert a recordable disc into the drive.

What worked for me was to download and install GnomeBaker (ver. 0.6.0). Surprisingly, GnomeBaker worked fine and successfully created a test audio CD. Under GnomeBaker's Edit menu --> select Preferences --> then take a look at the Devices tab. There you should see your CD drives and whether GnomeBaker can "Write CD-R" and/or "Write CD-RW." (In the case of my CD-RW drive info, both these boxes were checked without my intervention). 

I can't explain why GnomeBaker works and the other applications don't. Nor can I explain why  the same CD-RW drive creates audio CDs flawlessly under my other Linux distros (using K3b). The CD-R I was using as the recording medium was from a pack of TDK CD-Rs which have all been fine, so I don't believe the problem was caused by a faulty disc.    

I did see what you mentioned about the Permissions of the CD drives under Places --> Computer. (I have a CD-RW drive and a DVD-ROM read-only drive). My Permissions there are set the same as yours. I am not positive but I think that in order to change these settings, you would need to edit your [FONT="Courier New"][FONT="Fixedsys"]fstab[/FONT][/FONT] file, which is found in the [FONT="Courier New"][FONT="Fixedsys"]/etc/[/FONT] [/FONT]directory. You would have to be logged in as an Administrator and change settings via the command line, so I don't recommend that you try this unless you get a detailed how-to from someone more knowledgeable than me ... I've read some online info about editing the [FONT="Courier New"]fstab[/FONT] (=file system table) file and it looks a bit intimidating. 

HTH,
=david

---

### Post by koleoptero on 2008-02-17
For heaven's sake do not try to change permissions for the cdr. They are meant to be read-only. You can't read/write a cd, you can only burn it once with the proper tools.

Does your windows installation have problems with writing cds?

---

### Post by maxhoward on 2008-04-23
Have been away for awhile and am now back on this problem.  I created an .ogg file and tried burning an audio CD with Gnomebaker, but Gnomebaker wouldn't do it.  It started the process by creating the audio file it needed but then stopped with an error message.  I tried it again and noticed that a dialogue box called "Create Audio CD" came up with several options which I am not sure about.  For example "Speed"  was set for 4X and "Mode" was set for "Auto". Plus there were a couple of check boxes:  "Dummy Write"  and "Burn Free".   I don't know what these 4 items mean or what I should set them to.  I can't find any user instructions for GnomeBaker.

I looked at Gnomebaker -> Edit -> preferences -> Device Tab and the settings are the same as described in the previous reply.

To answer Koleoptero's reply, I have succesfully burned several CDs using this RW drive under WindowsXP.

Any more help will be greatly appreciated.

---

### Post by maxhoward on 2008-05-06
I finally discovered the problem.  My CD drive was bad.  It could read but not burn.  The new CD burner works fine and I was able to successfully burn an audio CD with GnomeBaker.

I apologize for bothering you all when the problem turned out to be hardware and not software or operator error.

Thanks for all the responses.

Maxhoward

---

