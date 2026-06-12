---
title: "VLC at startup"
date: 2011-07-07
forum: Multimedia Software
---

### Post by vodas89 on 2011-07-07
Hi there, 
I've got Xubuntu 11.04, VLC 1.1.9.
I'm working on some kind of streaming server and I would like to start VLC stream at startup in case of PC reboot (for instance after blackout).

I've made script to do that and append that script to init.d and use upadate-rc.d.

VLC don't work correctly because of some network issue (host unreachable, cannot make raw udp socket) but network and all its parts work correctly (for sure!!). 

Have you got some advice for me, please??

---

### Post by vodas89 on 2011-07-08
Noone ?

---

### Post by BicyclerBoy on 2011-07-08
ubuntu gnome has a tool that saves the state of machine (loaded apps) & re-instates at startup.
Gnome Menu:System/Preferences/Startup Applications Preferences "Options" tab

You can snapshot the current running apps or auto snapshot at every shutdown..

Script method:
There are ways of delaying VLC loading until other services load.
Could just use a time delay (crude)

The Gnome method does ensure the X server is running & network is up..

[http://www.thegeekstuff.com/2009/07/ubuntu-open-applications-automatically-during-system-startup/](http://www.thegeekstuff.com/2009/07/ubuntu-open-applications-automatically-during-system-startup/)

---

### Post by vodas89 on 2011-07-09
> **BicyclerBoy said:**
> ubuntu gnome has a tool that saves the state of machine (loaded apps) & re-instates at startup.
Gnome Menu:System/Preferences/Startup Applications Preferences "Options" tab

You can snapshot the current running apps or auto snapshot at every shutdown..

Script method:
There are ways of delaying VLC loading until other services load.
Could just use a time delay (crude)

The Gnome method does ensure the X server is running & network is up..

[http://www.thegeekstuff.com/2009/07/ubuntu-open-applications-automatically-during-system-startup/](http://www.thegeekstuff.com/2009/07/ubuntu-open-applications-automatically-during-system-startup/)


If I use the Gnome method, do i have to log in ? ... I wrote script that checking eth0 ip address and waiting until it get it.

Problem was that eth0 interface did not have an ip address in moment when vlc was started ... here's script i put into rc.local (or rc2.d -> multiuser runlevel)

logfile = /home/user/streamer/log_file
function loop {
        ipaddr=$(ifconfig | awk '/inet addr:/{if($2 !~ /127.0.0.1/) print $2}' | awk -F':' '{print $2}')
        if echo $ipaddr | grep -E '([0-9]+\.){3}[0-9]+' 
        then
                echo GOT IP ADDRESS >> $logfile
                echo starting vlc >> $logfile
                sudo -u qup vlc --vlm-conf /home/user/vlm_export --intf telnet -vvv --file-logging --logfile /home/user/vlc_log --file-caching 5000 --daemon 
        else
                echo GOT NO IP ADDRESS >> $logfile
                sleep 5
                loop
        fi
}

loop


Thank you for answers ... ;)

---

### Post by adammarleymtts on 2011-07-09
VLC is best Video player I can say.

---

### Post by BicyclerBoy on 2011-07-09
I don't know for sure but suspect that the Gnome startup apps method would only work if you logged in & gdm has drawn the desktop first.

I imagine VLC (the gui) would not run unless there is a X screen but you are using daemonised process.

If your method gives you any problems then have a look at how the mythbackend process is started, it runs/works before/without login but after DHCP  & other processes.

VLC is reliable but I find it annoying to use. (linux 1.0.6 & windows 1.1.0)
- multi-channel audio stereo downmix still seems wrong
- does not choose the right audio output device (windows) for multi-ch audio
- multi-ch audio to 5.1 virtual device (windows) does not work right (could be windows)
- forgets/turns off yadif filter after playing audio only..

---

