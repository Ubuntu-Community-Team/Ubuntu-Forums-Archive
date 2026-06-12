---
title: "backend problems (crashing?) - $20 reward"
date: 2009-03-19
forum: Mythbuntu
---

### Post by davidstoll on 2009-03-19
The backend seems to be running (from command prompt, ps -u mythtv, shows it is running), but I can't run the backend GUI nor the frontend.

When I run the backend, it pops up for a second (I can see the theme background, but no icons or text) and then dissapears.  Then the box to run mythfilldatabase comes up.

I will paypal $20 to whoever that can help me fix this and get my system back up and running.

I am a bit of a noob when it comes to linux, but I can basically get around.  If you need log files, let me know which ones.

Thank you!

---

### Post by nickrout on 2009-03-19
There is no backend gui so I assume you are talking about mythtv-setup. Please confirm.

Are you running it from the commandline? Or from mythbuntu-control-center?

Try running from the commandline and see if it spits errors at you.

---

### Post by davidstoll on 2009-03-19
> **nickrout said:**
> There is no backend gui so I assume you are talking about mythtv-setup. Please confirm.

Are you running it from the commandline? Or from mythbuntu-control-center?

Try running from the commandline and see if it spits errors at you.

Yes, mythtv-setup.  Sorry...like I said, I'm a noob and I get the lingo screwed up sometimes.

I am running it from the shortcut in the drop-down/run menu (like the start menu in Winblows) and also from the control center.

Running from command line was a good idea.

```
$ mythtv-setup
 * Stopping MythTV server: mythbackend          [ OK ] 
 * Restarting MythTV server: mythbackend          No /usr/bin/mythbackend found running; none killed.          [ OK ]
```

But, this is running...
```
$ ps -u mythtv
  PID TTY          TIME CMD
10458 ?        00:00:01 mythbackend
```

---

### Post by nickrout on 2009-03-19
hmm i'll have to look at my system when I am home.

---

### Post by davidstoll on 2009-03-19
Interestingly, I can hear the hard drive making noise, so I looked inside the recording directory and there is an mpg file (increasing in size)...so it is still recording shows.

I'm dead in the water as far as running the front end, accessing mythweb or running the mythtv-setup to access the tuner cards.

I would really appreciate any help...I'm dying here... ;(

---

### Post by Afkpuz on 2009-03-19
Hmm, well, I know that you need to stop the backend in order to enter the setup.  Try this in the command line

```
sudo killall mythbackend
```


Then, try running the backend setup.  If that fails, you might try reinstalling mythbackend via synaptic.

---

### Post by nickrout on 2009-03-19
perhaps try running mythfrontend from the command line and see what you get.

---

### Post by davidstoll on 2009-03-19
> **Afkpuz said:**
> Hmm, well, I know that you need to stop the backend in order to enter the setup.  Try this in the command line

```
sudo killall mythbackend
```


Then, try running the backend setup.  If that fails, you might try reinstalling mythbackend via synaptic.

The setup screen never came up when I did this...
```
$ sudo killall mythbackend
$ mythtv-setup
 * Stopping MythTV server: mythbackend                                          No /usr/bin/mythbackend found running; none killed.
                                                                         [ OK ]
 * Restarting MythTV server: mythbackend                                        No /usr/bin/mythbackend found running; none killed.
/usr/bin/mythbackend: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
```

When I tried to re-install the mythtv-backend I got this error from synaptic...
```
E: mythtv-backend: subprocess post-installation script returned error exit status 127
```

details...
```
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
david@MythBuntu:/var/log/mythtv$ sudo apt-get install mythtv-backend
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mythtv-backend is already the newest version.
The following packages were automatically installed and are no longer required:
  nvidia-180-kernel-source
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up mythtv-backend (0.21.0+trunk19951-0ubuntu0+mythbuntu1) ...
udev active, devices will be created in /dev/.static/dev/
rm: cannot remove `video0-': Read-only file system
mknod: `video0-': Read-only file system
makedev video0 c 81 0 root video 0660: failed
rm: cannot remove `video0-': Read-only file system
rm: cannot remove `radio0-': Read-only file system
mknod: `radio0-': Read-only file system
makedev radio0 c 81 64 root video 0660: failed
rm: cannot remove `radio0-': Read-only file system
rm: cannot remove `video1-': Read-only file system
mknod: `video1-': Read-only file system
makedev video1 c 81 1 root video 0660: failed
rm: cannot remove `video1-': Read-only file system
rm: cannot remove `radio1-': Read-only file system
mknod: `radio1-': Read-only file system
makedev radio1 c 81 65 root video 0660: failed
rm: cannot remove `radio1-': Read-only file system
rm: cannot remove `video2-': Read-only file system
mknod: `video2-': Read-only file system
makedev video2 c 81 2 root video 0660: failed
rm: cannot remove `video2-': Read-only file system
rm: cannot remove `radio2-': Read-only file system
mknod: `radio2-': Read-only file system
makedev radio2 c 81 66 root video 0660: failed
rm: cannot remove `radio2-': Read-only file system
rm: cannot remove `video3-': Read-only file system
mknod: `video3-': Read-only file system
makedev video3 c 81 3 root video 0660: failed
rm: cannot remove `video3-': Read-only file system
rm: cannot remove `radio3-': Read-only file system
mknod: `radio3-': Read-only file system
makedev radio3 c 81 67 root video 0660: failed
rm: cannot remove `radio3-': Read-only file system
rm: cannot remove `video4-': Read-only file system
mknod: `video4-': Read-only file system
makedev video4 c 81 4 root video 0660: failed
rm: cannot remove `video4-': Read-only file system
rm: cannot remove `radio4-': Read-only file system
mknod: `radio4-': Read-only file system
makedev radio4 c 81 68 root video 0660: failed
rm: cannot remove `radio4-': Read-only file system
rm: cannot remove `video5-': Read-only file system
mknod: `video5-': Read-only file system
makedev video5 c 81 5 root video 0660: failed
rm: cannot remove `video5-': Read-only file system
rm: cannot remove `radio5-': Read-only file system
mknod: `radio5-': Read-only file system
makedev radio5 c 81 69 root video 0660: failed
rm: cannot remove `radio5-': Read-only file system
rm: cannot remove `video6-': Read-only file system
mknod: `video6-': Read-only file system
makedev video6 c 81 6 root video 0660: failed
rm: cannot remove `video6-': Read-only file system
rm: cannot remove `radio6-': Read-only file system
mknod: `radio6-': Read-only file system
makedev radio6 c 81 70 root video 0660: failed
rm: cannot remove `radio6-': Read-only file system
rm: cannot remove `video7-': Read-only file system
mknod: `video7-': Read-only file system
makedev video7 c 81 7 root video 0660: failed
rm: cannot remove `video7-': Read-only file system
rm: cannot remove `radio7-': Read-only file system
mknod: `radio7-': Read-only file system
makedev radio7 c 81 71 root video 0660: failed
rm: cannot remove `radio7-': Read-only file system
rm: cannot remove `video8-': Read-only file system
mknod: `video8-': Read-only file system
makedev video8 c 81 8 root video 0660: failed
rm: cannot remove `video8-': Read-only file system
rm: cannot remove `radio8-': Read-only file system
mknod: `radio8-': Read-only file system
makedev radio8 c 81 72 root video 0660: failed
rm: cannot remove `radio8-': Read-only file system
rm: cannot remove `video9-': Read-only file system
mknod: `video9-': Read-only file system
makedev video9 c 81 9 root video 0660: failed
rm: cannot remove `video9-': Read-only file system
rm: cannot remove `radio9-': Read-only file system
mknod: `radio9-': Read-only file system
makedev radio9 c 81 73 root video 0660: failed
rm: cannot remove `radio9-': Read-only file system
rm: cannot remove `video10-': Read-only file system
mknod: `video10-': Read-only file system
makedev video10 c 81 10 root video 0660: failed
rm: cannot remove `video10-': Read-only file system
rm: cannot remove `radio10-': Read-only file system
mknod: `radio10-': Read-only file system
makedev radio10 c 81 74 root video 0660: failed
rm: cannot remove `radio10-': Read-only file system
rm: cannot remove `video11-': Read-only file system
mknod: `video11-': Read-only file system
makedev video11 c 81 11 root video 0660: failed
rm: cannot remove `video11-': Read-only file system
rm: cannot remove `radio11-': Read-only file system
mknod: `radio11-': Read-only file system
makedev radio11 c 81 75 root video 0660: failed
rm: cannot remove `radio11-': Read-only file system
rm: cannot remove `video12-': Read-only file system
mknod: `video12-': Read-only file system
makedev video12 c 81 12 root video 0660: failed
rm: cannot remove `video12-': Read-only file system
rm: cannot remove `radio12-': Read-only file system
mknod: `radio12-': Read-only file system
makedev radio12 c 81 76 root video 0660: failed
rm: cannot remove `radio12-': Read-only file system
rm: cannot remove `video13-': Read-only file system
mknod: `video13-': Read-only file system
makedev video13 c 81 13 root video 0660: failed
rm: cannot remove `video13-': Read-only file system
rm: cannot remove `radio13-': Read-only file system
mknod: `radio13-': Read-only file system
makedev radio13 c 81 77 root video 0660: failed
rm: cannot remove `radio13-': Read-only file system
rm: cannot remove `video14-': Read-only file system
mknod: `video14-': Read-only file system
makedev video14 c 81 14 root video 0660: failed
rm: cannot remove `video14-': Read-only file system
rm: cannot remove `radio14-': Read-only file system
mknod: `radio14-': Read-only file system
makedev radio14 c 81 78 root video 0660: failed
rm: cannot remove `radio14-': Read-only file system
rm: cannot remove `video15-': Read-only file system
mknod: `video15-': Read-only file system
makedev video15 c 81 15 root video 0660: failed
rm: cannot remove `video15-': Read-only file system
rm: cannot remove `radio15-': Read-only file system
mknod: `radio15-': Read-only file system
makedev radio15 c 81 79 root video 0660: failed
rm: cannot remove `radio15-': Read-only file system
rm: cannot remove `video16-': Read-only file system
mknod: `video16-': Read-only file system
makedev video16 c 81 16 root video 0660: failed
rm: cannot remove `video16-': Read-only file system
rm: cannot remove `radio16-': Read-only file system
mknod: `radio16-': Read-only file system
makedev radio16 c 81 80 root video 0660: failed
rm: cannot remove `radio16-': Read-only file system
rm: cannot remove `video17-': Read-only file system
mknod: `video17-': Read-only file system
makedev video17 c 81 17 root video 0660: failed
rm: cannot remove `video17-': Read-only file system
rm: cannot remove `radio17-': Read-only file system
mknod: `radio17-': Read-only file system
makedev radio17 c 81 81 root video 0660: failed
rm: cannot remove `radio17-': Read-only file system
rm: cannot remove `video18-': Read-only file system
mknod: `video18-': Read-only file system
makedev video18 c 81 18 root video 0660: failed
rm: cannot remove `video18-': Read-only file system
rm: cannot remove `radio18-': Read-only file system
mknod: `radio18-': Read-only file system
makedev radio18 c 81 82 root video 0660: failed
rm: cannot remove `radio18-': Read-only file system
rm: cannot remove `video19-': Read-only file system
mknod: `video19-': Read-only file system
makedev video19 c 81 19 root video 0660: failed
rm: cannot remove `video19-': Read-only file system
rm: cannot remove `radio19-': Read-only file system
mknod: `radio19-': Read-only file system
makedev radio19 c 81 83 root video 0660: failed
rm: cannot remove `radio19-': Read-only file system
rm: cannot remove `video20-': Read-only file system
mknod: `video20-': Read-only file system
makedev video20 c 81 20 root video 0660: failed
rm: cannot remove `video20-': Read-only file system
rm: cannot remove `radio20-': Read-only file system
mknod: `radio20-': Read-only file system
makedev radio20 c 81 84 root video 0660: failed
rm: cannot remove `radio20-': Read-only file system
rm: cannot remove `video21-': Read-only file system
mknod: `video21-': Read-only file system
makedev video21 c 81 21 root video 0660: failed
rm: cannot remove `video21-': Read-only file system
rm: cannot remove `radio21-': Read-only file system
mknod: `radio21-': Read-only file system
makedev radio21 c 81 85 root video 0660: failed
rm: cannot remove `radio21-': Read-only file system
rm: cannot remove `video22-': Read-only file system
mknod: `video22-': Read-only file system
makedev video22 c 81 22 root video 0660: failed
rm: cannot remove `video22-': Read-only file system
rm: cannot remove `radio22-': Read-only file system
mknod: `radio22-': Read-only file system
makedev radio22 c 81 86 root video 0660: failed
rm: cannot remove `radio22-': Read-only file system
rm: cannot remove `video23-': Read-only file system
mknod: `video23-': Read-only file system
makedev video23 c 81 23 root video 0660: failed
rm: cannot remove `video23-': Read-only file system
rm: cannot remove `radio23-': Read-only file system
mknod: `radio23-': Read-only file system
makedev radio23 c 81 87 root video 0660: failed
rm: cannot remove `radio23-': Read-only file system
rm: cannot remove `video24-': Read-only file system
mknod: `video24-': Read-only file system
makedev video24 c 81 24 root video 0660: failed
rm: cannot remove `video24-': Read-only file system
rm: cannot remove `radio24-': Read-only file system
mknod: `radio24-': Read-only file system
makedev radio24 c 81 88 root video 0660: failed
rm: cannot remove `radio24-': Read-only file system
rm: cannot remove `video25-': Read-only file system
mknod: `video25-': Read-only file system
makedev video25 c 81 25 root video 0660: failed
rm: cannot remove `video25-': Read-only file system
rm: cannot remove `radio25-': Read-only file system
mknod: `radio25-': Read-only file system
makedev radio25 c 81 89 root video 0660: failed
rm: cannot remove `radio25-': Read-only file system
rm: cannot remove `video26-': Read-only file system
mknod: `video26-': Read-only file system
makedev video26 c 81 26 root video 0660: failed
rm: cannot remove `video26-': Read-only file system
rm: cannot remove `radio26-': Read-only file system
mknod: `radio26-': Read-only file system
makedev radio26 c 81 90 root video 0660: failed
rm: cannot remove `radio26-': Read-only file system
rm: cannot remove `video27-': Read-only file system
mknod: `video27-': Read-only file system
makedev video27 c 81 27 root video 0660: failed
rm: cannot remove `video27-': Read-only file system
rm: cannot remove `radio27-': Read-only file system
mknod: `radio27-': Read-only file system
makedev radio27 c 81 91 root video 0660: failed
rm: cannot remove `radio27-': Read-only file system
rm: cannot remove `video28-': Read-only file system
mknod: `video28-': Read-only file system
makedev video28 c 81 28 root video 0660: failed
rm: cannot remove `video28-': Read-only file system
rm: cannot remove `radio28-': Read-only file system
mknod: `radio28-': Read-only file system
makedev radio28 c 81 92 root video 0660: failed
rm: cannot remove `radio28-': Read-only file system
rm: cannot remove `video29-': Read-only file system
mknod: `video29-': Read-only file system
makedev video29 c 81 29 root video 0660: failed
rm: cannot remove `video29-': Read-only file system
rm: cannot remove `radio29-': Read-only file system
mknod: `radio29-': Read-only file system
makedev radio29 c 81 93 root video 0660: failed
rm: cannot remove `radio29-': Read-only file system
rm: cannot remove `video30-': Read-only file system
mknod: `video30-': Read-only file system
makedev video30 c 81 30 root video 0660: failed
rm: cannot remove `video30-': Read-only file system
rm: cannot remove `radio30-': Read-only file system
mknod: `radio30-': Read-only file system
makedev radio30 c 81 94 root video 0660: failed
rm: cannot remove `radio30-': Read-only file system
rm: cannot remove `video31-': Read-only file system
mknod: `video31-': Read-only file system
makedev video31 c 81 31 root video 0660: failed
rm: cannot remove `video31-': Read-only file system
rm: cannot remove `radio31-': Read-only file system
mknod: `radio31-': Read-only file system
makedev radio31 c 81 95 root video 0660: failed
rm: cannot remove `radio31-': Read-only file system
rm: cannot remove `video32-': Read-only file system
mknod: `video32-': Read-only file system
makedev video32 c 81 32 root video 0660: failed
rm: cannot remove `video32-': Read-only file system
rm: cannot remove `radio32-': Read-only file system
mknod: `radio32-': Read-only file system
makedev radio32 c 81 96 root video 0660: failed
rm: cannot remove `radio32-': Read-only file system
rm: cannot remove `video33-': Read-only file system
mknod: `video33-': Read-only file system
makedev video33 c 81 33 root video 0660: failed
rm: cannot remove `video33-': Read-only file system
rm: cannot remove `radio33-': Read-only file system
mknod: `radio33-': Read-only file system
makedev radio33 c 81 97 root video 0660: failed
rm: cannot remove `radio33-': Read-only file system
rm: cannot remove `video34-': Read-only file system
mknod: `video34-': Read-only file system
makedev video34 c 81 34 root video 0660: failed
rm: cannot remove `video34-': Read-only file system
rm: cannot remove `radio34-': Read-only file system
mknod: `radio34-': Read-only file system
makedev radio34 c 81 98 root video 0660: failed
rm: cannot remove `radio34-': Read-only file system
rm: cannot remove `video35-': Read-only file system
mknod: `video35-': Read-only file system
makedev video35 c 81 35 root video 0660: failed
rm: cannot remove `video35-': Read-only file system
rm: cannot remove `radio35-': Read-only file system
mknod: `radio35-': Read-only file system
makedev radio35 c 81 99 root video 0660: failed
rm: cannot remove `radio35-': Read-only file system
rm: cannot remove `video36-': Read-only file system
mknod: `video36-': Read-only file system
makedev video36 c 81 36 root video 0660: failed
rm: cannot remove `video36-': Read-only file system
rm: cannot remove `radio36-': Read-only file system
mknod: `radio36-': Read-only file system
makedev radio36 c 81 100 root video 0660: failed
rm: cannot remove `radio36-': Read-only file system
rm: cannot remove `video37-': Read-only file system
mknod: `video37-': Read-only file system
makedev video37 c 81 37 root video 0660: failed
rm: cannot remove `video37-': Read-only file system
rm: cannot remove `radio37-': Read-only file system
mknod: `radio37-': Read-only file system
makedev radio37 c 81 101 root video 0660: failed
rm: cannot remove `radio37-': Read-only file system
rm: cannot remove `video38-': Read-only file system
mknod: `video38-': Read-only file system
makedev video38 c 81 38 root video 0660: failed
rm: cannot remove `video38-': Read-only file system
rm: cannot remove `radio38-': Read-only file system
mknod: `radio38-': Read-only file system
makedev radio38 c 81 102 root video 0660: failed
rm: cannot remove `radio38-': Read-only file system
rm: cannot remove `video39-': Read-only file system
mknod: `video39-': Read-only file system
makedev video39 c 81 39 root video 0660: failed
rm: cannot remove `video39-': Read-only file system
rm: cannot remove `radio39-': Read-only file system
mknod: `radio39-': Read-only file system
makedev radio39 c 81 103 root video 0660: failed
rm: cannot remove `radio39-': Read-only file system
rm: cannot remove `video40-': Read-only file system
mknod: `video40-': Read-only file system
makedev video40 c 81 40 root video 0660: failed
rm: cannot remove `video40-': Read-only file system
rm: cannot remove `radio40-': Read-only file system
mknod: `radio40-': Read-only file system
makedev radio40 c 81 104 root video 0660: failed
rm: cannot remove `radio40-': Read-only file system
rm: cannot remove `video41-': Read-only file system
mknod: `video41-': Read-only file system
makedev video41 c 81 41 root video 0660: failed
rm: cannot remove `video41-': Read-only file system
rm: cannot remove `radio41-': Read-only file system
mknod: `radio41-': Read-only file system
makedev radio41 c 81 105 root video 0660: failed
rm: cannot remove `radio41-': Read-only file system
rm: cannot remove `video42-': Read-only file system
mknod: `video42-': Read-only file system
makedev video42 c 81 42 root video 0660: failed
rm: cannot remove `video42-': Read-only file system
rm: cannot remove `radio42-': Read-only file system
mknod: `radio42-': Read-only file system
makedev radio42 c 81 106 root video 0660: failed
rm: cannot remove `radio42-': Read-only file system
rm: cannot remove `video43-': Read-only file system
mknod: `video43-': Read-only file system
makedev video43 c 81 43 root video 0660: failed
rm: cannot remove `video43-': Read-only file system
rm: cannot remove `radio43-': Read-only file system
mknod: `radio43-': Read-only file system
makedev radio43 c 81 107 root video 0660: failed
rm: cannot remove `radio43-': Read-only file system
rm: cannot remove `video44-': Read-only file system
mknod: `video44-': Read-only file system
makedev video44 c 81 44 root video 0660: failed
rm: cannot remove `video44-': Read-only file system
rm: cannot remove `radio44-': Read-only file system
mknod: `radio44-': Read-only file system
makedev radio44 c 81 108 root video 0660: failed
rm: cannot remove `radio44-': Read-only file system
rm: cannot remove `video45-': Read-only file system
mknod: `video45-': Read-only file system
makedev video45 c 81 45 root video 0660: failed
rm: cannot remove `video45-': Read-only file system
rm: cannot remove `radio45-': Read-only file system
mknod: `radio45-': Read-only file system
makedev radio45 c 81 109 root video 0660: failed
rm: cannot remove `radio45-': Read-only file system
rm: cannot remove `video46-': Read-only file system
mknod: `video46-': Read-only file system
makedev video46 c 81 46 root video 0660: failed
rm: cannot remove `video46-': Read-only file system
rm: cannot remove `radio46-': Read-only file system
mknod: `radio46-': Read-only file system
makedev radio46 c 81 110 root video 0660: failed
rm: cannot remove `radio46-': Read-only file system
rm: cannot remove `video47-': Read-only file system
mknod: `video47-': Read-only file system
makedev video47 c 81 47 root video 0660: failed
rm: cannot remove `video47-': Read-only file system
rm: cannot remove `radio47-': Read-only file system
mknod: `radio47-': Read-only file system
makedev radio47 c 81 111 root video 0660: failed
rm: cannot remove `radio47-': Read-only file system
rm: cannot remove `video48-': Read-only file system
mknod: `video48-': Read-only file system
makedev video48 c 81 48 root video 0660: failed
rm: cannot remove `video48-': Read-only file system
rm: cannot remove `radio48-': Read-only file system
mknod: `radio48-': Read-only file system
makedev radio48 c 81 112 root video 0660: failed
rm: cannot remove `radio48-': Read-only file system
rm: cannot remove `video49-': Read-only file system
mknod: `video49-': Read-only file system
makedev video49 c 81 49 root video 0660: failed
rm: cannot remove `video49-': Read-only file system
rm: cannot remove `radio49-': Read-only file system
mknod: `radio49-': Read-only file system
makedev radio49 c 81 113 root video 0660: failed
rm: cannot remove `radio49-': Read-only file system
rm: cannot remove `video50-': Read-only file system
mknod: `video50-': Read-only file system
makedev video50 c 81 50 root video 0660: failed
rm: cannot remove `video50-': Read-only file system
rm: cannot remove `radio50-': Read-only file system
mknod: `radio50-': Read-only file system
makedev radio50 c 81 114 root video 0660: failed
rm: cannot remove `radio50-': Read-only file system
rm: cannot remove `video51-': Read-only file system
mknod: `video51-': Read-only file system
makedev video51 c 81 51 root video 0660: failed
rm: cannot remove `video51-': Read-only file system
rm: cannot remove `radio51-': Read-only file system
mknod: `radio51-': Read-only file system
makedev radio51 c 81 115 root video 0660: failed
rm: cannot remove `radio51-': Read-only file system
rm: cannot remove `video52-': Read-only file system
mknod: `video52-': Read-only file system
makedev video52 c 81 52 root video 0660: failed
rm: cannot remove `video52-': Read-only file system
rm: cannot remove `radio52-': Read-only file system
mknod: `radio52-': Read-only file system
makedev radio52 c 81 116 root video 0660: failed
rm: cannot remove `radio52-': Read-only file system
rm: cannot remove `video53-': Read-only file system
mknod: `video53-': Read-only file system
makedev video53 c 81 53 root video 0660: failed
rm: cannot remove `video53-': Read-only file system
rm: cannot remove `radio53-': Read-only file system
mknod: `radio53-': Read-only file system
makedev radio53 c 81 117 root video 0660: failed
rm: cannot remove `radio53-': Read-only file system
rm: cannot remove `video54-': Read-only file system
mknod: `video54-': Read-only file system
makedev video54 c 81 54 root video 0660: failed
rm: cannot remove `video54-': Read-only file system
rm: cannot remove `radio54-': Read-only file system
mknod: `radio54-': Read-only file system
makedev radio54 c 81 118 root video 0660: failed
rm: cannot remove `radio54-': Read-only file system
rm: cannot remove `video55-': Read-only file system
mknod: `video55-': Read-only file system
makedev video55 c 81 55 root video 0660: failed
rm: cannot remove `video55-': Read-only file system
rm: cannot remove `radio55-': Read-only file system
mknod: `radio55-': Read-only file system
makedev radio55 c 81 119 root video 0660: failed
rm: cannot remove `radio55-': Read-only file system
rm: cannot remove `video56-': Read-only file system
mknod: `video56-': Read-only file system
makedev video56 c 81 56 root video 0660: failed
rm: cannot remove `video56-': Read-only file system
rm: cannot remove `radio56-': Read-only file system
mknod: `radio56-': Read-only file system
makedev radio56 c 81 120 root video 0660: failed
rm: cannot remove `radio56-': Read-only file system
rm: cannot remove `video57-': Read-only file system
mknod: `video57-': Read-only file system
makedev video57 c 81 57 root video 0660: failed
rm: cannot remove `video57-': Read-only file system
rm: cannot remove `radio57-': Read-only file system
mknod: `radio57-': Read-only file system
makedev radio57 c 81 121 root video 0660: failed
rm: cannot remove `radio57-': Read-only file system
rm: cannot remove `video58-': Read-only file system
mknod: `video58-': Read-only file system
makedev video58 c 81 58 root video 0660: failed
rm: cannot remove `video58-': Read-only file system
rm: cannot remove `radio58-': Read-only file system
mknod: `radio58-': Read-only file system
makedev radio58 c 81 122 root video 0660: failed
rm: cannot remove `radio58-': Read-only file system
rm: cannot remove `video59-': Read-only file system
mknod: `video59-': Read-only file system
makedev video59 c 81 59 root video 0660: failed
rm: cannot remove `video59-': Read-only file system
rm: cannot remove `radio59-': Read-only file system
mknod: `radio59-': Read-only file system
makedev radio59 c 81 123 root video 0660: failed
rm: cannot remove `radio59-': Read-only file system
rm: cannot remove `video60-': Read-only file system
mknod: `video60-': Read-only file system
makedev video60 c 81 60 root video 0660: failed
rm: cannot remove `video60-': Read-only file system
rm: cannot remove `radio60-': Read-only file system
mknod: `radio60-': Read-only file system
makedev radio60 c 81 124 root video 0660: failed
rm: cannot remove `radio60-': Read-only file system
rm: cannot remove `video61-': Read-only file system
mknod: `video61-': Read-only file system
makedev video61 c 81 61 root video 0660: failed
rm: cannot remove `video61-': Read-only file system
rm: cannot remove `radio61-': Read-only file system
mknod: `radio61-': Read-only file system
makedev radio61 c 81 125 root video 0660: failed
rm: cannot remove `radio61-': Read-only file system
rm: cannot remove `video62-': Read-only file system
mknod: `video62-': Read-only file system
makedev video62 c 81 62 root video 0660: failed
rm: cannot remove `video62-': Read-only file system
rm: cannot remove `radio62-': Read-only file system
mknod: `radio62-': Read-only file system
makedev radio62 c 81 126 root video 0660: failed
rm: cannot remove `radio62-': Read-only file system
rm: cannot remove `video63-': Read-only file system
mknod: `video63-': Read-only file system
makedev video63 c 81 63 root video 0660: failed
rm: cannot remove `video63-': Read-only file system
rm: cannot remove `radio63-': Read-only file system
mknod: `radio63-': Read-only file system
makedev radio63 c 81 127 root video 0660: failed
rm: cannot remove `radio63-': Read-only file system
rm: cannot remove `radio': Read-only file system
rm: cannot remove `vtx0-': Read-only file system
mknod: `vtx0-': Read-only file system
makedev vtx0 c 81 192 root video 0660: failed
rm: cannot remove `vtx0-': Read-only file system
rm: cannot remove `vbi0-': Read-only file system
mknod: `vbi0-': Read-only file system
makedev vbi0 c 81 224 root video 0660: failed
rm: cannot remove `vbi0-': Read-only file system
rm: cannot remove `vtx1-': Read-only file system
mknod: `vtx1-': Read-only file system
makedev vtx1 c 81 193 root video 0660: failed
rm: cannot remove `vtx1-': Read-only file system
rm: cannot remove `vbi1-': Read-only file system
mknod: `vbi1-': Read-only file system
makedev vbi1 c 81 225 root video 0660: failed
rm: cannot remove `vbi1-': Read-only file system
rm: cannot remove `vtx2-': Read-only file system
mknod: `vtx2-': Read-only file system
makedev vtx2 c 81 194 root video 0660: failed
rm: cannot remove `vtx2-': Read-only file system
rm: cannot remove `vbi2-': Read-only file system
mknod: `vbi2-': Read-only file system
makedev vbi2 c 81 226 root video 0660: failed
rm: cannot remove `vbi2-': Read-only file system
rm: cannot remove `vtx3-': Read-only file system
mknod: `vtx3-': Read-only file system
makedev vtx3 c 81 195 root video 0660: failed
rm: cannot remove `vtx3-': Read-only file system
rm: cannot remove `vbi3-': Read-only file system
mknod: `vbi3-': Read-only file system
makedev vbi3 c 81 227 root video 0660: failed
rm: cannot remove `vbi3-': Read-only file system
rm: cannot remove `vtx4-': Read-only file system
mknod: `vtx4-': Read-only file system
makedev vtx4 c 81 196 root video 0660: failed
rm: cannot remove `vtx4-': Read-only file system
rm: cannot remove `vbi4-': Read-only file system
mknod: `vbi4-': Read-only file system
makedev vbi4 c 81 228 root video 0660: failed
rm: cannot remove `vbi4-': Read-only file system
rm: cannot remove `vtx5-': Read-only file system
mknod: `vtx5-': Read-only file system
makedev vtx5 c 81 197 root video 0660: failed
rm: cannot remove `vtx5-': Read-only file system
rm: cannot remove `vbi5-': Read-only file system
mknod: `vbi5-': Read-only file system
makedev vbi5 c 81 229 root video 0660: failed
rm: cannot remove `vbi5-': Read-only file system
rm: cannot remove `vtx6-': Read-only file system
mknod: `vtx6-': Read-only file system
makedev vtx6 c 81 198 root video 0660: failed
rm: cannot remove `vtx6-': Read-only file system
rm: cannot remove `vbi6-': Read-only file system
mknod: `vbi6-': Read-only file system
makedev vbi6 c 81 230 root video 0660: failed
rm: cannot remove `vbi6-': Read-only file system
rm: cannot remove `vtx7-': Read-only file system
mknod: `vtx7-': Read-only file system
makedev vtx7 c 81 199 root video 0660: failed
rm: cannot remove `vtx7-': Read-only file system
rm: cannot remove `vbi7-': Read-only file system
mknod: `vbi7-': Read-only file system
makedev vbi7 c 81 231 root video 0660: failed
rm: cannot remove `vbi7-': Read-only file system
rm: cannot remove `vtx8-': Read-only file system
mknod: `vtx8-': Read-only file system
makedev vtx8 c 81 200 root video 0660: failed
rm: cannot remove `vtx8-': Read-only file system
rm: cannot remove `vbi8-': Read-only file system
mknod: `vbi8-': Read-only file system
makedev vbi8 c 81 232 root video 0660: failed
rm: cannot remove `vbi8-': Read-only file system
rm: cannot remove `vtx9-': Read-only file system
mknod: `vtx9-': Read-only file system
makedev vtx9 c 81 201 root video 0660: failed
rm: cannot remove `vtx9-': Read-only file system
rm: cannot remove `vbi9-': Read-only file system
mknod: `vbi9-': Read-only file system
makedev vbi9 c 81 233 root video 0660: failed
rm: cannot remove `vbi9-': Read-only file system
rm: cannot remove `vtx10-': Read-only file system
mknod: `vtx10-': Read-only file system
makedev vtx10 c 81 202 root video 0660: failed
rm: cannot remove `vtx10-': Read-only file system
rm: cannot remove `vbi10-': Read-only file system
mknod: `vbi10-': Read-only file system
makedev vbi10 c 81 234 root video 0660: failed
rm: cannot remove `vbi10-': Read-only file system
rm: cannot remove `vtx11-': Read-only file system
mknod: `vtx11-': Read-only file system
makedev vtx11 c 81 203 root video 0660: failed
rm: cannot remove `vtx11-': Read-only file system
rm: cannot remove `vbi11-': Read-only file system
mknod: `vbi11-': Read-only file system
makedev vbi11 c 81 235 root video 0660: failed
rm: cannot remove `vbi11-': Read-only file system
rm: cannot remove `vtx12-': Read-only file system
mknod: `vtx12-': Read-only file system
makedev vtx12 c 81 204 root video 0660: failed
rm: cannot remove `vtx12-': Read-only file system
rm: cannot remove `vbi12-': Read-only file system
mknod: `vbi12-': Read-only file system
makedev vbi12 c 81 236 root video 0660: failed
rm: cannot remove `vbi12-': Read-only file system
rm: cannot remove `vtx13-': Read-only file system
mknod: `vtx13-': Read-only file system
makedev vtx13 c 81 205 root video 0660: failed
rm: cannot remove `vtx13-': Read-only file system
rm: cannot remove `vbi13-': Read-only file system
mknod: `vbi13-': Read-only file system
makedev vbi13 c 81 237 root video 0660: failed
rm: cannot remove `vbi13-': Read-only file system
rm: cannot remove `vtx14-': Read-only file system
mknod: `vtx14-': Read-only file system
makedev vtx14 c 81 206 root video 0660: failed
rm: cannot remove `vtx14-': Read-only file system
rm: cannot remove `vbi14-': Read-only file system
mknod: `vbi14-': Read-only file system
makedev vbi14 c 81 238 root video 0660: failed
rm: cannot remove `vbi14-': Read-only file system
rm: cannot remove `vtx15-': Read-only file system
mknod: `vtx15-': Read-only file system
makedev vtx15 c 81 207 root video 0660: failed
rm: cannot remove `vtx15-': Read-only file system
rm: cannot remove `vbi15-': Read-only file system
mknod: `vbi15-': Read-only file system
makedev vbi15 c 81 239 root video 0660: failed
rm: cannot remove `vbi15-': Read-only file system
rm: cannot remove `vtx16-': Read-only file system
mknod: `vtx16-': Read-only file system
makedev vtx16 c 81 208 root video 0660: failed
rm: cannot remove `vtx16-': Read-only file system
rm: cannot remove `vbi16-': Read-only file system
mknod: `vbi16-': Read-only file system
makedev vbi16 c 81 240 root video 0660: failed
rm: cannot remove `vbi16-': Read-only file system
rm: cannot remove `vtx17-': Read-only file system
mknod: `vtx17-': Read-only file system
makedev vtx17 c 81 209 root video 0660: failed
rm: cannot remove `vtx17-': Read-only file system
rm: cannot remove `vbi17-': Read-only file system
mknod: `vbi17-': Read-only file system
makedev vbi17 c 81 241 root video 0660: failed
rm: cannot remove `vbi17-': Read-only file system
rm: cannot remove `vtx18-': Read-only file system
mknod: `vtx18-': Read-only file system
makedev vtx18 c 81 210 root video 0660: failed
rm: cannot remove `vtx18-': Read-only file system
rm: cannot remove `vbi18-': Read-only file system
mknod: `vbi18-': Read-only file system
makedev vbi18 c 81 242 root video 0660: failed
rm: cannot remove `vbi18-': Read-only file system
rm: cannot remove `vtx19-': Read-only file system
mknod: `vtx19-': Read-only file system
makedev vtx19 c 81 211 root video 0660: failed
rm: cannot remove `vtx19-': Read-only file system
rm: cannot remove `vbi19-': Read-only file system
mknod: `vbi19-': Read-only file system
makedev vbi19 c 81 243 root video 0660: failed
rm: cannot remove `vbi19-': Read-only file system
rm: cannot remove `vtx20-': Read-only file system
mknod: `vtx20-': Read-only file system
makedev vtx20 c 81 212 root video 0660: failed
rm: cannot remove `vtx20-': Read-only file system
rm: cannot remove `vbi20-': Read-only file system
mknod: `vbi20-': Read-only file system
makedev vbi20 c 81 244 root video 0660: failed
rm: cannot remove `vbi20-': Read-only file system
rm: cannot remove `vtx21-': Read-only file system
mknod: `vtx21-': Read-only file system
makedev vtx21 c 81 213 root video 0660: failed
rm: cannot remove `vtx21-': Read-only file system
rm: cannot remove `vbi21-': Read-only file system
mknod: `vbi21-': Read-only file system
makedev vbi21 c 81 245 root video 0660: failed
rm: cannot remove `vbi21-': Read-only file system
rm: cannot remove `vtx22-': Read-only file system
mknod: `vtx22-': Read-only file system
makedev vtx22 c 81 214 root video 0660: failed
rm: cannot remove `vtx22-': Read-only file system
rm: cannot remove `vbi22-': Read-only file system
mknod: `vbi22-': Read-only file system
makedev vbi22 c 81 246 root video 0660: failed
rm: cannot remove `vbi22-': Read-only file system
rm: cannot remove `vtx23-': Read-only file system
mknod: `vtx23-': Read-only file system
makedev vtx23 c 81 215 root video 0660: failed
rm: cannot remove `vtx23-': Read-only file system
rm: cannot remove `vbi23-': Read-only file system
mknod: `vbi23-': Read-only file system
makedev vbi23 c 81 247 root video 0660: failed
rm: cannot remove `vbi23-': Read-only file system
rm: cannot remove `vtx24-': Read-only file system
mknod: `vtx24-': Read-only file system
makedev vtx24 c 81 216 root video 0660: failed
rm: cannot remove `vtx24-': Read-only file system
rm: cannot remove `vbi24-': Read-only file system
mknod: `vbi24-': Read-only file system
makedev vbi24 c 81 248 root video 0660: failed
rm: cannot remove `vbi24-': Read-only file system
rm: cannot remove `vtx25-': Read-only file system
mknod: `vtx25-': Read-only file system
makedev vtx25 c 81 217 root video 0660: failed
rm: cannot remove `vtx25-': Read-only file system
rm: cannot remove `vbi25-': Read-only file system
mknod: `vbi25-': Read-only file system
makedev vbi25 c 81 249 root video 0660: failed
rm: cannot remove `vbi25-': Read-only file system
rm: cannot remove `vtx26-': Read-only file system
mknod: `vtx26-': Read-only file system
makedev vtx26 c 81 218 root video 0660: failed
rm: cannot remove `vtx26-': Read-only file system
rm: cannot remove `vbi26-': Read-only file system
mknod: `vbi26-': Read-only file system
makedev vbi26 c 81 250 root video 0660: failed
rm: cannot remove `vbi26-': Read-only file system
rm: cannot remove `vtx27-': Read-only file system
mknod: `vtx27-': Read-only file system
makedev vtx27 c 81 219 root video 0660: failed
rm: cannot remove `vtx27-': Read-only file system
rm: cannot remove `vbi27-': Read-only file system
mknod: `vbi27-': Read-only file system
makedev vbi27 c 81 251 root video 0660: failed
rm: cannot remove `vbi27-': Read-only file system
rm: cannot remove `vtx28-': Read-only file system
mknod: `vtx28-': Read-only file system
makedev vtx28 c 81 220 root video 0660: failed
rm: cannot remove `vtx28-': Read-only file system
rm: cannot remove `vbi28-': Read-only file system
mknod: `vbi28-': Read-only file system
makedev vbi28 c 81 252 root video 0660: failed
rm: cannot remove `vbi28-': Read-only file system
rm: cannot remove `vtx29-': Read-only file system
mknod: `vtx29-': Read-only file system
makedev vtx29 c 81 221 root video 0660: failed
rm: cannot remove `vtx29-': Read-only file system
rm: cannot remove `vbi29-': Read-only file system
mknod: `vbi29-': Read-only file system
makedev vbi29 c 81 253 root video 0660: failed
rm: cannot remove `vbi29-': Read-only file system
rm: cannot remove `vtx30-': Read-only file system
mknod: `vtx30-': Read-only file system
makedev vtx30 c 81 222 root video 0660: failed
rm: cannot remove `vtx30-': Read-only file system
rm: cannot remove `vbi30-': Read-only file system
mknod: `vbi30-': Read-only file system
makedev vbi30 c 81 254 root video 0660: failed
rm: cannot remove `vbi30-': Read-only file system
rm: cannot remove `vtx31-': Read-only file system
mknod: `vtx31-': Read-only file system
makedev vtx31 c 81 223 root video 0660: failed
rm: cannot remove `vtx31-': Read-only file system
rm: cannot remove `vbi31-': Read-only file system
mknod: `vbi31-': Read-only file system
makedev vbi31 c 81 255 root video 0660: failed
rm: cannot remove `vbi31-': Read-only file system
rm: cannot remove `video': Read-only file system
rm: cannot remove `vbi': Read-only file system
rm: cannot remove `winradio0-': Read-only file system
mknod: `winradio0-': Read-only file system
makedev winradio0 c 82 0 root video 0660: failed
rm: cannot remove `winradio0-': Read-only file system
rm: cannot remove `winradio1-': Read-only file system
mknod: `winradio1-': Read-only file system
makedev winradio1 c 82 1 root video 0660: failed
rm: cannot remove `winradio1-': Read-only file system
rm: cannot remove `vtx-': Read-only file system
mknod: `vtx-': Read-only file system
makedev vtx c 83 0 root video 0660: failed
rm: cannot remove `vtx-': Read-only file system
rm: cannot remove `vttuner-': Read-only file system
mknod: `vttuner-': Read-only file system
makedev vttuner c 83 16 root video 0660: failed
rm: cannot remove `vttuner-': Read-only file system
 * Starting MythTV server: mythbackend                                                                                                /usr/bin/mythbackend: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory
invoke-rc.d: initscript mythtv-backend, action "start" failed.
dpkg: error processing mythtv-backend (--configure):
 subprocess post-installation script returned error exit status 127
Errors were encountered while processing:
 mythtv-backend
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

---

### Post by davidstoll on 2009-03-19
> **nickrout said:**
> perhaps try running mythfrontend from the command line and see what you get.

This is what happens...

```
$ mythfrontend
/usr/bin/mythfrontend.real: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

---

### Post by nickrout on 2009-03-19
libGL.so.1 is provided by a number of packages including nvidia-glx and libgl1-mesa-glx

what does glxinfo tell you?

---

### Post by davidstoll on 2009-03-19
> **nickrout said:**
> libGL.so.1 is provided by a number of packages including nvidia-glx and libgl1-mesa-glx

what does glxinfo tell you?

I'm not sure what that is or how to run it.
I searched for a file with that name and didn't come up with anything.

If you mean the page in the nvidia X server settings....
"Fail to query the GLX server vendor."

---

### Post by nickrout on 2009-03-19
hmm there appears to be something wrong with your X setup if nvdia-settings can't find any glx information.

glxinfo is a commandline rogram that tests what GL settings your computer is using.

I assume you have an nVidia card because you talk about running the nvidia-settings program.

could you tell me what version of the nvidia drivers you are running, and can you also tell me what driver X is using.

the former you should get by running

dpkg -l |grep nvidia

the latter by looking at /var/log/Xorg.0.log and seeing if it is using the nv (open source) driver or the nvidia (closed source) driver. Its a long file, I would look at it using the less program.

```
less /var/log/Xorg.0.log
```

then use the / key and type in the pattern you want to search for, then enter. To find the next occurrence press n. To get out press q.

---

### Post by azmyth on 2009-03-19
Sounds like you're missing some dependencies. What I would do is boot Mythubuntu in non-gui mode so you can get to the command prompt. I'd then do a sudo apt-get update then sudo apt-get upgrade. Are you using the standard mythbuntu packages or are you using the ones from avenard? Make sure you have installed nvidia-180-kernel-sources, nvidia-glx-180, nvidia-180-modaliases

---

### Post by davidstoll on 2009-03-19
> **nickrout said:**
> hmm there appears to be something wrong with your X setup if nvdia-settings can't find any glx information.

glxinfo is a commandline rogram that tests what GL settings your computer is using.

I assume you have an nVidia card because you talk about running the nvidia-settings program.

could you tell me what version of the nvidia drivers you are running, and can you also tell me what driver X is using.

the former you should get by running

dpkg -l |grep nvidia

the latter by looking at /var/log/Xorg.0.log and seeing if it is using the nv (open source) driver or the nvidia (closed source) driver. Its a long file, I would look at it using the less program.

```
less /var/log/Xorg.0.log
```

then use the / key and type in the pattern you want to search for, then enter. To find the next occurrence press n. To get out press q.

I am using 180...at least that is what the restricted drivers manager had activated, but I tried to change to 177 or 173 and it errored out.  After that error, the restricted drivers manager no longer shows 180 as active and now I'm afraid to reboot....and now the restricted drivers manager isn't coming up.  It's just saying "searching for available drivers...".

Here is what that command shows...

```
$ dpkg -l |grep nvidia
ii  nvidia-173-modaliases                      173.14.12-1-0ubuntu5.1                  Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-177-modaliases                      177.82-0ubuntu0.1                       Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-180-kernel-source                   180.22-0ubuntu1~intrepid1               NVIDIA binary kernel module source
ii  nvidia-180-libvdpau                        180.22-0ubuntu1~intrepid1               Video Decode and Presentation API for Unix
ii  nvidia-180-modaliases                      180.22-0ubuntu1~intrepid1               Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-71-modaliases                       71.86.04-0ubuntu10                      Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-96-modaliases                       96.43.09-0ubuntu1.1                     Modaliases for the NVIDIA binary X.Org driver
ii  nvidia-common                              0.2.4                                   Find obsolete NVIDIA drivers
rc  nvidia-glx-173                             173.14.12-1-0ubuntu5.1                  NVIDIA binary Xorg driver
ic  nvidia-glx-177                             177.82-0ubuntu0.1                       NVIDIA binary Xorg driver
ic  nvidia-glx-180                             180.22-0ubuntu1~intrepid1               NVIDIA binary Xorg driver
ii  nvidia-kernel-common                       20051028+1+nmu2ubuntu2                  NVIDIA binary kernel module common files
ii  nvidia-settings                            177.78-0ubuntu2.1                       Tool of configuring the NVIDIA graphics driver

```

---

### Post by davidstoll on 2009-03-19
> **azmyth said:**
> Sounds like you're missing some dependencies. What I would do is boot Mythubuntu in non-gui mode so you can get to the command prompt. I'd then do a sudo apt-get update then sudo apt-get upgrade. Are you using the standard mythbuntu packages or are you using the ones from avenard? Make sure you have installed nvidia-180-kernel-sources, nvidia-glx-180, nvidia-180-modaliases

If I try to reinstall those packages, synaptic gives me this error:
E: /var/cache/apt/archives/nvidia-glx-180_180.22-0ubuntu1~intrepid1_amd64.deb: subprocess pre-installation script returned error exit status 2

And I also get a similar long error log similar to the long log I posted in #8 on page 1.

[http://ubuntuforums.org/showpost.php?p=6925774&postcount=8](http://ubuntuforums.org/showpost.php?p=6925774&postcount=8)

By the way, I've never heard of avenard.

I'm really afraid to reboot at this point.  Do you think I should still do that?  I don't want to loose my GUI...I'm not as good with the command line.  Also, I'm not even sure how to boot to a command line anyway.

But...I'm willing to try.  I just need a little hand holding.

I do appreciate your help.

---

### Post by azmyth on 2009-03-19
When did you upgrade the nvidia drivers, have you rebooted since you upgraded the drivers. Once you upgrade the drivers, the system gets really flaky until you reboot. When I upgrade drivers, I end up doing a sudo shutdown -h now command.

---

### Post by davidstoll on 2009-03-20
> **azmyth said:**
> When did you upgrade the nvidia drivers, have you rebooted since you upgraded the drivers. Once you upgrade the drivers, the system gets really flaky until you reboot. When I upgrade drivers, I end up doing a sudo shutdown -h now command.

Ok, so I rebooted and now I'm running in low graphics mode.

Do you think I should clean house with regards to my graphics drivers and then reinstall?  If so, can someone suggest what to remove to clean things up and what command to use?

---

### Post by theophile on 2009-03-20
What gfx card do you have? If you're not sure, you'll find the device ID in 'lspci -v'

You can usually fix the libGl.so error by completely removing all nVidia related packages and installing from nVidia's binary driver installer rather than the Ubuntu packages. I've had nothing but trouble with the Ubuntu packages myself.

What I would do:
1. CTL+ALT+F2 will get you to the console so you can actually get something done.
2. apt-get remove nvidia*
3. apt-get install envyng-gtk
4. envyng -t
5. From the menu select "1" and go through the prompts to automatically install the latest nVidia drivers it detects for your card.
6. After it's done, reboot.

If you still end up booting into low graphics mode, it's very likely a problem with your xorg.conf. If you have problems after the above, paste here your /etc/X11/xorg.conf file so we can have a look.

---

### Post by davidstoll on 2009-03-20
> **theophile said:**
> What gfx card do you have? If you're not sure, you'll find the device ID in 'lspci -v'

You can usually fix the libGl.so error by completely removing all nVidia related packages and installing from nVidia's binary driver installer rather than the Ubuntu packages. I've had nothing but trouble with the Ubuntu packages myself.

What I would do:
1. CTL+ALT+F2 will get you to the console so you can actually get something done.
2. apt-get remove nvidia*
3. apt-get install envyng-gtk
4. envyng -t
5. From the menu select "1" and go through the prompts to automatically install the latest nVidia drivers it detects for your card.
6. After it's done, reboot.

If you still end up booting into low graphics mode, it's very likely a problem with your xorg.conf. If you have problems after the above, paste here your /etc/X11/xorg.conf file so we can have a look.

I get the same error every time I try to install anything...including your sugestions...in ctrl+alt+F2...
```
$sudo apt-get remove nvidia*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting nvidia-96-kernel-source for regex 'nvidia*'
Note, selecting nvidia-177-kernel-source for regex 'nvidia*'
Note, selecting nvidia-glx-new-envy for regex 'nvidia*'
Note, selecting nvidia-kernel-common for regex 'nvidia*'
Note, selecting nvidia-common for regex 'nvidia*'
Note, selecting nvidia-cg-toolkit for regex 'nvidia*'
Note, selecting nvidia-glx-dev-legacy for regex 'nvidia*'
Note, selecting nvidia-180-libvdpau for regex 'nvidia*'
Note, selecting nvidia-glx-96-dev for regex 'nvidia*'
Note, selecting nvidia-glx-dev-new for regex 'nvidia*'
Note, selecting nvidia-glx-dev for regex 'nvidia*'
Note, selecting nvidia-new-kernel-source for regex 'nvidia*'
Note, selecting nvidia-71-kernel-source for regex 'nvidia*'
Note, selecting nvidia-glx-ia32 for regex 'nvidia*'
Note, selecting nvidia-177-modaliases for regex 'nvidia*'
Note, selecting nvidia-glx-new for regex 'nvidia*'
Note, selecting nvidia-glx-173-dev for regex 'nvidia*'
Note, selecting nvidia-glx-dev-new-envy for regex 'nvidia*'
Note, selecting nvidia-glx-src for regex 'nvidia*'
Note, selecting nvidia-glx-lrm-dev for regex 'nvidia*'
Note, selecting nvidia-kernel-source for regex 'nvidia*'
Note, selecting nvidia-glx-envy for regex 'nvidia*'
Note, selecting nvidia-173-kernel-source for regex 'nvidia*'
Note, selecting nvidia-glx-173 for regex 'nvidia*'
Note, selecting nvidia-glx-180 for regex 'nvidia*'
Note, selecting nvidia-glx-177 for regex 'nvidia*'
Note, selecting nvidia-glx-177-dev for regex 'nvidia*'
Note, selecting nvidia-180-libvdpau-dev for regex 'nvidia*'
Note, selecting nvidia-180-modaliases for regex 'nvidia*'
Note, selecting nvidia-glx-legacy for regex 'nvidia*'
Note, selecting nvidia-glx-dev-legacy-envy for regex 'nvidia*'
Note, selecting nvidia-96-modaliases for regex 'nvidia*'
Note, selecting nvidia-glx-71-dev for regex 'nvidia*'
Note, selecting nvidia-xconfig for regex 'nvidia*'
Note, selecting nvidia-180-kernel-source for regex 'nvidia*'
Note, selecting nvidia-glx-legacy-envy for regex 'nvidia*'
Note, selecting nvidia-kernel-src for regex 'nvidia*'
Note, selecting nvidia-kernel-source-envy for regex 'nvidia*'
Note, selecting nvidia-71-modaliases for regex 'nvidia*'
Note, selecting nvidia-legacy-kernel-source for regex 'nvidia*'
Note, selecting nvidia-glx-dev-envy for regex 'nvidia*'
Note, selecting nvidia-legacy-kernel-source-envy for regex 'nvidia*'
Note, selecting nvidia-new-kernel-source-envy for regex 'nvidia*'
Note, selecting nvidia-glx-71 for regex 'nvidia*'
Note, selecting nvidia-glx-96 for regex 'nvidia*'
Note, selecting nvidia-173-modaliases for regex 'nvidia*'
Note, selecting nvidia-glx for regex 'nvidia*'
Note, selecting nvidia-glx-180-dev for regex 'nvidia*'
Note, selecting nvidia-settings for regex 'nvidia*'
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libglu1-mesa-dev: Depends: libgl1-mesa-dev or
                             libgl-dev
  libmyth-0.22-0: Depends: nvidia-180-libvdpau but it is not going to be installed
  libqt3-mt-dev: Depends: libgl1-mesa-dev or
                          libgl-dev
  libqt4-opengl-dev: Depends: libgl1-mesa-dev or
                              libgl-dev
  xlibmesa-gl-dev: Depends: libgl1-mesa-dev
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
$
$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  nvidia-96-modaliases nvidia-71-modaliases
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  nvidia-glx-180
The following NEW packages will be installed:
  nvidia-glx-180
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B/15.7MB of archives.
After this operation, 49.6MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 171549 files and directories currently installed.)
Unpacking nvidia-glx-180 (from .../nvidia-glx-180_180.22-0ubuntu1~intrepid1_amd64.deb) ...
dpkg-divert: mismatch on divert-to
  when removing `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/nvidia/libGL.so.1.2.xserver-xorg-core by nvidia-glx-177'
  found `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx-177'
dpkg-divert: `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx-180' clashes with `diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/nvidia/libGL.so.1.2.xlibmesa by nvidia-glx-177'
dpkg: error processing /var/cache/apt/archives/nvidia-glx-180_180.22-0ubuntu1~intrepid1_amd64.deb (--unpack):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/nvidia-glx-180_180.22-0ubuntu1~intrepid1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
$
$ sudo apt-get install envyng-gtk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  envyng-gtk: Depends: envyng-core (>= 2.0.1) but it is not going to be installed
  nvidia-glx-180-dev: Depends: nvidia-glx-180 (>= 180.22) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
$
```

I do the sudo apt-get -f install, but it doesn't help.

I think I may be doomed to re-install.

---

### Post by azmyth on 2009-03-20
I noticed this in your logs libmyth-0.22-0. I assume you have Mythtv 0.22 installed. 0.22 isn't a stable version. I suggest making a db backup and uninstall myth 0.22. Reboot then try to reinstall envyng-gtk?

_Which video card are you using?_

---

### Post by davidstoll on 2009-03-23
> **azmyth said:**
> I noticed this in your logs libmyth-0.22-0. I assume you have Mythtv 0.22 installed. 0.22 isn't a stable version. I suggest making a db backup and uninstall myth 0.22. Reboot then try to reinstall envyng-gtk?

_Which video card are you using?_

I'm using the Nvidia 8500GT.

How do you uninstall a trunk by the way?  Just remove the data source in synaptic?

---

### Post by nickrout on 2009-03-23
Once you install and run trunk you cannot go back. It changes the format of the database and there is no return unles you backed up your database. As it says on the mythbuntu weekly builds page.

> Also, there have been requests for trunk builds of mythtv. Many users opt to use trunk for features only available in development versions. It is also a good way to help with MythTV testing. Please note that these builds are not as optimized as regular builds to make it easier to debug them, so you may run into performance problems. By using the trunk builds, you sacrifice the stability afforded by a regular release cycle. If you are currently on a regular release, backup your MySQL database prior to enabling trunk builds. **There is no returning to regular releases after enabling trunk**.

Might have been relevant to tell us you were running trunk from the start!

---

