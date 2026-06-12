---
title: "mythbuntu - Step by Step instructions"
date: 2013-01-17
forum: Mythbuntu
---

### Post by jfaberna on 2013-01-17
When I was trying to find step by step instructions to install mythtv, I didn’t find any current ones that helped me.  So now that I have mythtv working buy using mythbuntu, I thought I document what I did.

My hardware for the backend was a 2nd generation Core i7 PC using the built-in GFX and a PCIe capture card/tuner.

Installing mythbuntu – combined frontend and backend – HTPC

1.	I downloaded and created as CDROM with mythbuntu 12.04.1 from the [http://www.mythbuntu.org/](http://www.mythbuntu.org/) site. I used an actual CDROM because I’ve had problems with startup USB images on some PC hardware.
2.	Booted the CDROM and select install
3.	Check ‘Download updates while installing’ and ‘Install this third-party software’.
4.	Erase everything and reinstall if you had anything on your drive.
5.	Use the entire disk
6.	Select location and keyboard layout
7.	Enter login info.
8.	Select Primary ‘Backend w/ Frontend’.
9.	For Services, SSH and Samba are already checked. I added MythTV service because I will also support remote frontends.
10.	Select your type of remote.
11.	Go get a beer (optional)
12.	Reboot when finished.
13.	System will boot to the frontend, but you need to ESC and exit so you can do some configuration of the system and backend.
14.	My tuner card is a Hauppauge HVR-2250 and when I checked dmesg, I see the firmware file is missing, so I found it online and copied that into the right directory.  Firmware info is found in the Wiki for mythtv.
15.	Reboot with firmware now loaded and ESC’ed out of frontend to configure Myth Backend.
16.	On General I set all the IP address to my machines IP address instead of ‘localhost’
17.	I configured my capture card remembering that I had to add 2 of them since my card is a dual tuner and is seen by Linux as 2 adapters.
18.	Next I configured video sources to use my account on SchedulesDirect.org.
19.	Configured Input Connections so the cards were linked to the video sources.
20.	I chose to scan for channels for each tuner card. Not sure if I had to.
21.	I exited out of backend setup, entered my password to restart the backend, and said yes to re-run the database setup.
22.	Now I started the mythtv frontend.
23.	I went into setup and configured my audio and theme.
24.	I tested ‘Watch TV’ and it worked, also tested the Program Guide under Manage Recording.
25.	Next I ran update manager after exiting the Frontend.
26.	Rebooted after updating system and everything still works.
27.	I copied down the information in /etc/mythtv/mysql.txt for any remote frontend configuration.

The next part is to setup a remote frontend on a 3rd Generation Core i3 (NUC) PC

Installing mythbuntu – frontend remote

1.	Booted the CDROM and select install
2.	Check ‘Download updates while installing’ and ‘Install this third-party software’.
3.	Erase everything and reinstall if you had anything on your drive.
4.	Use the entire disk
5.	Select location and keyboard layout
6.	Enter login info.
7.	Select Primary ‘Frontend’.
8.	For Services, leave as is.
9.	On Masterbackend info, test connection, 0000 is the right Security Key.  You should see success.
10.	 Complete install and reboot.
11.	Frontend automatically starts.
12.	Select location and language
13.	Next change Database host IP to match your backend IP.
14.	Change database password to match /etc/mythtv/mysql.txt on the backend
15.	You should now be able to look at your library of recorded shows or Live TV.
16.	After I tested some, I exited the frontend and ran update manager to get the system up to date.

---

