---
title: "No UPnP backends found - LiveCD frontend to working master backend"
date: 2009-11-06
forum: Mythbuntu
---

### Post by B34N on 2009-11-06
I'm new to Mythbuntu and recently got Mythbuntu to work as a frontend and backend on an older machine.  Now I want that machine to run as a dedicated backend and I would like to install frontends on all of my other machines.  I thought it would be wise to get the kinks out and get everything running on a LiveCD before permanently installing the frontends.  (I chose this route because I unsuccessfully tried setting up MythTV once before and I couldn't figure out how to fully remove it to start from scratch)

I started off the LiveCD and connected to my wireless network.  I chose "Run Mythbuntu Live CD frontend" which brought up the "Mythbuntu Live Session Configuration".  I entered in the requested information, hit the "Test connection" button and was returned "Successful".  I was not able to  get a successful response using the server's hostname (old-HTPC) so I used the IP address.  After clicking on "Start session" I was asked for my preferred language and then got the message "No UPnP backends found".  After choosing "ok" on the message I was shown the "Database Configuration" screen, which did not include the hostname or password I entered at the "Mythbuntu Live Session Configuration" window.  I entered the IP address in the hostname and the password in the password.  (I believe the ping test was active by default)  After paging past the next few configuration screens I got the message "Could not connect to the master backend server -- is it running?  Is the IP address set for it in the setup program correct".  I went back and verified that everything was correct and after once again paging through the configuration screens I received the same message.

I was able to use firefox on the LiveCD to access MythWeb via the IP address.  I also don't know why the hostname isn't working.  Ping and MythWeb only worked using the IP address.


Thank you!

---

### Post by klc5555 on 2009-11-06
> **st8ofmi9d said:**
> I'm new to Mythbuntu and recently got Mythbuntu to work as a frontend and backend on an older machine.  Now I want that machine to run as a dedicated backend and I would like to install frontends on all of my other machines.  I thought it would be wise to get the kinks out and get everything running on a LiveCD before permanently installing the frontends.  (I chose this route because I unsuccessfully tried setting up MythTV once before and I couldn't figure out how to fully remove it to start from scratch)

I started off the LiveCD and connected to my wireless network.  I chose "Run Mythbuntu Live CD frontend" which brought up the "Mythbuntu Live Session Configuration".  I entered in the requested information, hit the "Test connection" button and was returned "Successful".  I was not able to  get a successful response using the server's hostname (old-HTPC) so I used the IP address.  After clicking on "Start session" I was asked for my preferred language and then got the message "No UPnP backends found".  After choosing "ok" on the message I was shown the "Database Configuration" screen, which did not include the hostname or password I entered at the "Mythbuntu Live Session Configuration" window.  I entered the IP address in the hostname and the password in the password.  (I believe the ping test was active by default)  After paging past the next few configuration screens I got the message "Could not connect to the master backend server -- is it running?  Is the IP address set for it in the setup program correct".  I went back and verified that everything was correct and after once again paging through the configuration screens I received the same message.

I was able to use firefox on the LiveCD to access MythWeb via the IP address.  I also don't know why the hostname isn't working.  Ping and MythWeb only worked using the IP address.


Thank you!

By verifying "everything was correct" you set the backend ip to a real ip, not localhost or 127.0.0.1 (in both spots on the backend general setup page); put 0000 as the PIN number in the backend's setup; and turned on the MySQL service in the "services" tab in the Mythbuntu Control Center? The password you used was the backend's MySQL password and not the backend's user account password?

Hostname doesn't work because your home network is not set up to dish hostnames to the machines on your network or use them for resolution. If this becomes really a problem worth solving at some point, there are a variety of ways to do it depending on how the home network is set up. Easiest may be (after an actual OS installation) to edit the /etc/hosts file on each machine with the other machines' ip addresses and hostnames. On a really small network, just using the ip addresses is likely the simplest.

---

### Post by B34N on 2009-11-06
> **klc5555 said:**
> By verifying "everything was correct" you set the backend ip to a real ip, not localhost or 127.0.0.1 (in both spots on the backend general setup page); put 0000 as the PIN number in the backend's setup
That was it.  I was only verifying that "everything was correct" on the frontend.  I checked the backend and I setup the backend ip addresses to externally addressable addresses.  I also set the PIN to 0000.

After making those changes I was able to get further but there was still one more thing to correct.  I needed to change the time zone on the frontend to match the timezone on the backend.  Until I did that it just exited.  I figured it out by reading the logs. (I posted this in case someone else finds this in a search to solve the same issues)


> **klc5555 said:**
> Hostname doesn't work because your home network is not set up to dish hostnames to the machines on your network or use them for resolution. If this becomes really a problem worth solving at some point, there are a variety of ways to do it depending on how the home network is set up. Easiest may be (after an actual OS installation) to edit the /etc/hosts file on each machine with the other machines' ip addresses and hostnames. On a really small network, just using the ip addresses is likely the simplest.

This is something that I want to fix.  The IP addresses are not static.  I guess I'll do some searching on how to fix it.

After that I will need to install the frontends on other machines.  When I use Ubuntu's "Add/Remove" programs to install MythTV it wants to install both the frontend and backend.

---

### Post by klc5555 on 2009-11-06
> **st8ofmi9d said:**
> 

After that I will need to install the frontends on other machines.  When I use Ubuntu's "Add/Remove" programs to install MythTV it wants to install both the frontend and backend.

Use apt-get to install specifically "mythtv-frontend" and "mythtv-common" on top of some Ubuntu or other, and you should be in business. apt-get will install library dependencies, but shouldn't burden you with all the backend and MySQL junk that a pure frontend machine doesn't need.

---

### Post by B34N on 2009-11-06
> **klc5555 said:**
> Use apt-get to install specifically "mythtv-frontend" and "mythtv-common" on top of some Ubuntu or other, and you should be in business. apt-get will install library dependencies, but shouldn't burden you with all the backend and MySQL junk that a pure frontend machine doesn't need.

Thank you but doesn't the frontend also need MySQL?
[http://www.mythtv.org/wiki/Frequently_Asked_Questions#Well_then.2C_what_about_this_MySQL_thing.3F](http://www.mythtv.org/wiki/Frequently_Asked_Questions#Well_then.2C_what_about_this_MySQL_thing.3F)

---

