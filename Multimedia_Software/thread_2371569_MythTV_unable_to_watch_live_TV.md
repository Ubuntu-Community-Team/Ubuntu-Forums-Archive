---
title: "MythTV unable to watch live TV"
date: 2017-09-16
forum: Multimedia Software
---

### Post by doggie015 on 2017-09-16
Hi,

I'm a relatively new Mythbuntu user, but I've managed to successfully set up the live TV tuner to the point where I can see EPG listings broadcast from the station, however, whenever I try to actually watch live TV, it tries to fire up, but it fails going back to the menu. I'm running on a Toshiba Satellite L300 using the KBA01020 USB DVB-T tuner.

Looking at the logs, the relevant part from the backend appears to be

> 
[LIST]
[*][COLOR=#333333]Sep 16 13:35:46 jay-Satellite-L300 mythbackend: mythbackend[1286]: E TVRecEvent recorders/dvbchannel.cpp:1133 (GetUncorrectedBlockCount) DVBChan[1](/dev/dvb/adapter0/frontend0): Getting Frontend uncorrected block count failed.#012#011#011#011eno: Operation not supported (95)[/COLOR]
[*][COLOR=#333333]Sep 16 13:35:46 jay-Satellite-L300 mythbackend: mythbackend[1286]: W TVRecEvent recorders/dvbsignalmonitor.cpp:97 (DVBSignalMonitor) DVBSigMon[1](/dev/dvb/adapter0/frontend0): Cannot count Uncorrected Blocks#012#011#011#011eno: Operation not supported (95)[/COLOR]
[/LIST]


You can find the full logs for both the backend and frontend at [https://pastebin.com/ejDgvrdi](https://pastebin.com/ejDgvrdi) if required

Any ideas?

---

### Post by deadflowr on 2017-09-16
Make sure your Mythtv directory you created is writable.
What does 
```
ls -la /home/jay/MythTV
```
currently show?

The design of myth is to always record, even when running livetv.
(what is recorded during the live tv is automatically erased after a set time, unless record is pushed)
If it can't write, it can't record.

---

### Post by doggie015 on 2017-09-16
> **deadflowr said:**
> Make sure your Mythtv directory you created is writable.
What does 
```
ls -la /home/jay/MythTV
```
currently show?

The design of myth is to always record, even when running livetv.
(what is recorded during the live tv is automatically erased after a set time, unless record is pushed)
If it can't write, it can't record.

It shows the following

> Total 8

drwxrwxr-x 2 jay jay 4096 Sep 16 13:45 .

drwxr-xr-x 21 jay jay 4096 Sep 26 14:58 ..

I suspect that chmod may be needed... can you change directory permissions with it?

EDIT: chmod 775 /home/jay/MythTV -R tried - no result.

---

### Post by deadflowr on 2017-09-16
Try chown and making mythtv the group
```
chown -R jay:mythtv /home/jay/MythTV
```

Edit: more here:
[https://www.mythtv.org/wiki/Troubleshooting:Filesystem_Permissions]("https://www.mythtv.org/wiki/Troubleshooting:Filesystem_Permissions")

probably better

---

### Post by doggie015 on 2017-09-16
No dice. The backend is running as mythtv, the frontend as jay, both are in the mythtv group.

ls -la /home/jay/MythTV output

> 
drwxrwxr-x 2 jay mythtv 4096 Sep 16 16:03 .

drwxr-xr-x 21 jay mythtv 4096 Sep 16 16:02 .. 

---

### Post by MoebusNet on 2017-09-16
I just went through this because my LinHES OS SSD died 4 months after the warranty expired. This time I started with Ubuntu then installed the mythtv package from Ubuntu's repository. I ran into the same installation loop as you, could never get past the initial country, etc. screens. This is what worked for me:

The default password on Ubuntu for the mythtv database isn't mythtv.

Check the '/etc/mythtv/config.xml' file. The password will be there. Example:

```
gedit /etc/mythtv/config.xml
```

Copy down the username & password that is in the file. You can go ahead and close gedit (or whatever text editor you used) and the terminal; you can always reopen if needed. Now start Mythtv Backend Setup and use the username and password you copied from the '/etc/mythtv/config.xml' file.

Alternatively, if youu want to use a different username and password for the mythtv database, you can
```
gksudo gedit /etc/mythtv/config.xml
``` and change the username and password as desired. Save the changes in gedit (or whatever text editor), close everything and use that username & password for Mythtv Backend Setup.

I just used the default username and the random password assigned by Ubuntu's mythtv package. It all worked from there. Make sure you at least set up the Default Storage Group, or it still won't work: [https://www.mythtv.org/wiki/Configuring_MythTV](https://www.mythtv.org/wiki/Configuring_MythTV)

---

