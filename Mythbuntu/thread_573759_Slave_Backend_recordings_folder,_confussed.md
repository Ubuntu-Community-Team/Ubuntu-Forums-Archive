---
title: "Slave Backend recordings folder, confussed"
date: 2007-10-11
forum: Mythbuntu
---

### Post by dannyboy79 on 2007-10-11
Hello,
I just added a SBE/FE  to my current Feisty MBE/FE. Since I have a PVR-500 on the SBE/FE I will need to specify a recording directory to hold the recordings that the PVR-500 does. I thought I understand that I need to "export" the recording directory as an NFS share from the MBE/FE so that my SBE/FE can mount it to a folder and when mythtv starts recording it will write that file to the folder that is being shared via NFS from the MBE/FE. Well I did that and tonight when I try to view it in Recorded Programs within Mythtv, it says that the file is missing? I also tried viewing it thru XboxMediaCenter thru my xbox and it also never opened to view. Can someone please clarify how I should setup a SBE/FE so that all my recordings are kept the MBE/FE???

Thanks.

Oh, I am running Feisty on the MBE/FE
and Gutsy (mythbuntu control center) on the SBE/FE.
The database appears as though the shows were recorded but something isn't right since I can't find them on Mythweb thru Firefox on the MBE/FE.

 I will check soon to see if I can view the recordings on the MBE/FE thru the FE but I can't right now because mythfilldatabase is running and it's my understanding that mythbackend gets stopped while this is running.

---

### Post by superm1 on 2007-10-12
Actually they don't need to store a common directory.  You can just keep all the respective recordings on different boxes.  They are streamed via native myth protocol, not NFS if you don't mount NFS.  Native myth protocol is supposed to be faster anyhow.

---

### Post by dannyboy79 on 2007-10-12
well how do I get these 2 recordings to be able to watch them. the MBE/FE says that they can't be found just like mythweb. ALso, I am using a usb WIFI adapter and I click on recordings folder and it takes forever to open. Is this because WIFI? It's supposedly 54Mbps and so is my Netgear WIFI Router. In fact it says it can't even be found trying to view on the SBE/FE either? What do I do?

UPDATE
Well I am just disgusted that this didn't work, my recordings are no where??? The database is populated with teh recording info but no recording. If a folder is shared via NFS and mounted to the recording dir of the SBE, shouldn't the SBE write the recording to that share? It didn't, when I look in that folder on the MBE, I only see 6 .mpg's created on 10/11/07, when I should have 8. So they didn't get recorded. I completely don't understand what's going on???? 

Any help or explaination would be appreciated. I went into mythweb and deleted the shows so that they don't show up in my database anymore but I sure would liek to know how other's handle writing to a NFS server......


My NFS exports file was this:
/media/400gb/mythtv    192.168.0.6(rw,no_root_squash,async)

and my fstab on the SBE was this: 192.168.0.3:/media/400gb/mythtv        /var/lib/mythtv/recordings      nfs    i                          ntr,rsize=8192,wsize=8192,async,nfsvers=3,bg,actimeo=0,tcp

and when I was on the SBE, I issued an ls -la to view the contents of the /var/lib/mythtv/recordings folder and sure enough, all my recordings that are located on the MBE were there proving that the NFS share was mounted correctly. So what did I do wrong? 

I do see this in the SBE log about my 2 shows:
2007-10-11 19:00:08.789 TVRec(2): Changing from None to RecordingOnly
2007-10-11 19:00:09.111 TVRec(2): HW Tuner: 2->2
2007-10-11 19:00:11.267 TFW, Error: Opening file '/var/lib/mythtv/recordings/2005_20071011190000.mpg'.
                        eno: Permission denied (13)
2007-10-11 19:00:11.268 TVRec(2) Error: RingBuffer '/var/lib/mythtv/recordings/2005_20071011190000.mpg' not open...
2007-10-11 19:00:11.289 TVRec(2): Changing from RecordingOnly to None
2007-10-11 19:00:11.316 Finished recording Survivor: China "Ride the Workhorse 'Til the Tail Falls Off": channel 2005
2007-10-11 19:00:11.338 scheduler: Finished recording: Survivor: China "Ride the Workhorse 'Til the Tail Falls Off": channel 2005
2007-10-11 19:00:12.155 TVRec(3): Changing from None to RecordingOnly
2007-10-11 19:00:12.196 TVRec(3): HW Tuner: 3->3
2007-10-11 19:00:12.646 TFW, Error: Opening file '/var/lib/mythtv/recordings/2012_20071011190000.mpg'.
                        eno: Permission denied (13)
2007-10-11 19:00:12.647 TVRec(3) Error: RingBuffer '/var/lib/mythtv/recordings/2012_20071011190000.mpg' not open...
2007-10-11 19:00:12.654 TVRec(3): Changing from RecordingOnly to None
2007-10-11 19:00:12.716 Finished recording Ugly Betty "Betty's Wait Problem": channel 2012
2007-10-11 19:00:12.743 scheduler: Finished recording: Ugly Betty "Betty's Wait Problem": channel 2012
2007-10-11 22:03:15.442 Preview Error: Previewer file '/var/lib/mythtv/recordings/2005_20071011190000.mpg' is not valid.
2007-10-11 22:03:15.444 MainServer: Failed to make preview image.
2007-10-11 22:03:32.069 Preview Error: Previewer file '/var/lib/mythtv/recordings/2012_20071011190000.mpg' is not valid.
2007-10-11 22:03:32.070 MainServer: Failed to make preview image.
2007-10-11 22:11:03.933 Preview Error: Previewer file '/var/lib/mythtv/recordings/2012_20071011190000.mpg' is not valid.


but the permissions on the /var/lib/mythtv/recordings are:
drwxrwsr-x  2 mythtv mythtv 4096 2007-10-10 22:36 recordings

so please please please help...

I am also seeing this in the log
2007-10-11 12:57:25.851 Connecting to master server: 192.168.0.3:6543
2007-10-11 12:57:25.910 Connection to master server timed out.
Is this again related to using WIFI instead of 100mbit? I download a lot of stuff so could that be using most of the bandwidth and not allow mythtv any bandwidth?

---

### Post by dannyboy79 on 2007-10-12
another update. I now have set the SBE to just save it's recordings in /var/lib/mythtv/recordings. It saved it there and I can see it thru Nautilus but when I am in mythweb, there is no preview (like a .png file BUT I can see the .mpg.png on the SBE in the recordings folder.) and also when I click on it I am returned with this:
foo.mpg does not exist in the recordings directory.

This is also the case when trying to watch them thry the MBE/FE, it shows the show there, but when I click on it to watch it, screen goes black and then just returns back to the previous screen.

I CAN HOWEVER watch the recordings on the SBE/FE, so that's at least working!

So, you stated that I could leave recordings on each of their BE but what do I need to do to gfet this working??? WHen i look in the log of the SBE, it shows no errors like before with write permissions. 

As I stated above, I would like to have all recordings on what MBE but it's not working with NFS and even now it's not working just writing to it's own locaql drive??? Please help.

---

### Post by dannyboy79 on 2007-10-12
any other Mythtv Users with Slave BE/FE and Master BE/FE that can help please?

---

### Post by superm1 on 2007-10-14
Okay from what I gather, this is boiling down to permissions.

You are indeed properly exporting the nfs share, however you aren't mounting it rw.

In the fstab, near all those other options, add a** rw** to the list.

Unmount and remount it all.

Afterward, do a ls -alh on the directory and see what user and group are listed.

---

### Post by dannyboy79 on 2007-11-25
mario, can you help mne again please? I am getting an issue of not being able to view my recordings on my Master FE/BE which the recordings are stored on the Slave FE/BE. I am getting this error in mythweb: "2005_20071119210000.mpg does not exist in the recordings directory." despite it actually ebing there on the Slave FE/BE. I thought at one time it was bcause I didn't have the ip set correctly on the slave BE/FE but it's set to it's static ip. What am I doing wrong?

---

### Post by dannyboy79 on 2007-11-27
can anyone help me with this? I am having issues accessing recordings that are stored on the slave be/fe from the main be/fe. when I click on a show in mythweb "recorded programs" it states that the file is not in the recordings directory but it's there. the ip is set correctly within mythtv-setup. I am using xubuntu 7.10 and mythbuntu control center. It has a pvr-500 in it. Any help please?

---

