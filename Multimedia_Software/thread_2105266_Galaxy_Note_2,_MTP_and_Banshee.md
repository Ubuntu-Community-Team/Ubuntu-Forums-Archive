---
title: "Galaxy Note 2, MTP and Banshee"
date: 2013-01-15
forum: Multimedia Software
---

### Post by benlawlor85 on 2013-01-15
Hi all,
This is my first post on here, i have been using linux for about 6 months now. Migrating from OSX (hackintosh) to Mint. and then to 12.04 64bit. I had several things i needed to work when moving from OSX to ubuntu, one of the most important was music. I chose Banshee as it seemed most feature full.

I recently brought a Samsung Galaxy Note 2, and would like to copy my music to it. I tried several weeks ago to no avail. and had settled on using the new Google music system but im finding problems with that and since moving to ubuntu form mint it wants so re upload my 6000+ songs. 

So now i want to do it properly. I want it to work like an iphone would work with iTunes!
Before i did anything when i plugged the phone in two external drives would mount. but i cannot acesss anything on them, one is for the internal memory and the second for the sd card. the odd thing is i can see files and folders in the root of each.

So i followed this guide:
[http://askubuntu.com/questions/183482/getting-photos-and-music-on-off-samsung-google-galaxy-nexus-ice-cream-sandwich](http://askubuntu.com/questions/183482/getting-photos-and-music-on-off-samsung-google-galaxy-nexus-ice-cream-sandwich)

which didnt work.i get the following error:-
"Could not display "/media/androiddevice".
Error: Error when getting information for file '/media/androiddevice': Transport endpoint is not connected
Please select another viewer and try again.

I have looked at several other forums and they seem to think the following in of interest:-
ben@ben-ubuntu:~$ df
df: `/media/androiddevice': Transport endpoint is not connected
Filesystem     1K-blocks      Used Available Use% Mounted on
/dev/sda1      235558704  32080972 191512036  15% /
udev             2011632         4   2011628   1% /dev
tmpfs             808176       964    807212   1% /run
none                5120         0      5120   0% /run/lock
none             2020432      2284   2018148   1% /run/shm
/dev/sdb3      480614104 299860360 156339896  66% /media/3


ben@ben-ubuntu:~$ ls -l /media
ls: cannot access /media/androiddevice: Transport endpoint is not connected
total 8
drwxr-xr-x 18 ben  ben  4096 Dec 18 18:21 3
d?????????  ? ?    ?       ?            ? androiddevice
drwxr-xr-x  2 root root 4096 Dec 18 20:14 sdb3



im presuming that its not mounting properly, but im not sure what to do next.

ideally i would like to be able to sync the phone with banshee and keep play lists, ratings, play counts etc and even add the play counts back to the banshee play count. Just as itunes does with an iphone.

Sorry for a mammoth post. and hope someone can help


Ben

---

### Post by azangru on 2013-01-15
Sorry that I can't answer your exact question, but if nothing else helps you can always upload your music to your phone using AirDroid. It doesn't do syncing though, I'm afraid.

---

### Post by Lantau on 2013-03-02
Ive just bought a Note 2 and had similar problems in so much as it would connect but only show the root contents but not any folder contents. Additionally Nautilus saw it as a music device and Ubuntu automatically started Rythmbox. The clue came when I hovered the mouse over the device listing in the left hand pane of Nautilus, it said "gphoto2://[usb.....]. It appeared that Ubuntu assumed it to be a photo device. 
Once connected, the Note 2 notification pane displays the usb symbol. By swiping down and selecting the usb symbol it gives you the option to connect as a media device (MTP) or camera (PTP). Although the MTP seemed more appropriate for me it appeared that Ubuntu assumed it was a camera in any case. When I selected PTP Nautilus was much happier, faster, and allowed me to transfer files as I required. The Note 2 now appears as a device in Rythumbox whereas it didn't when I connected as a MTP.:confused:
This doesn't help you regarding the iTunes type functionality but it may help you at least get connected.

Update: Just tried both Banshee and Rythmbox to sync the Note 2. Banshee didn't see the device and Rythmbox keeps crashing within a couple of seconds of initiating a transfer. :(

---

### Post by DannStarr on 2013-03-16
I appreciate this doesn't answer your exact question, but it may set you in the right direction:[http://www.android.gs/mount-google-nexus-4-mtp-sd-card-on-ubuntu-and-other-linux-computers/](http://www.android.gs/mount-google-nexus-4-mtp-sd-card-on-ubuntu-and-other-linux-computers/)

---

### Post by amtrakuk on 2013-06-18
As the OP I have also migrated from Mac to Ubuntu - mainly due to samba compatability issues.   I have 2 mobiles a Iphone 3GS and a Samsung Galaxy 2.   Im trying to "Sync" my music library I migrated from iTunes to Rhythmbox with both devices.   The iphone seems to show more signs of success as in it appears to copy the music over but after the sync the iphone doesn't show the changes and also it seems to screw up what music you have on there!  Thinking forward I have just tried my works phone (Samsung Galaxy IIs).  This shows up in Rhythmbox but as soon as I try syncing, Rhythmbox crashes.
I'm happy to move from iPhone to the Samsung but how do I get Rhythmbox to sync my music?
Thanks

This resolved the issue for me - [http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html](http://www.webupd8.org/2012/12/how-to-mount-android-40-ubuntu-go-mtpfs.html)

---

