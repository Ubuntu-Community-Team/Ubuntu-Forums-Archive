---
title: "Remote Desktop server stopped working after upgrade to 10.10"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by comthre3 on 2010-10-11
Well I guess the topic says it all. I've recently upgraded to Maverick from Lucid all went smoothly until i restarted and realized that the remote desktop server included stopped functioning all of a sudden. tried other vnc servers with no luck, can someone walk me through it. I've looked at a couple of forums, and googled with not much help. any help would be appreciated. 

Thanks

---

### Post by magira on 2010-10-11
> **comthre3 said:**
> Well I guess the topic says it all. I've recently upgraded to Maverick from Lucid all went smoothly until i restarted and realized that the remote desktop server included stopped functioning all of a sudden. tried other vnc servers with no luck, can someone walk me through it. I've looked at a couple of forums, and googled with not much help. any help would be appreciated. 

Thanks


This is exactly my own problem! Couldnt describe it othervise.

---

### Post by tanshu on 2010-10-11
Same here :( ... hope someone can figure out what happened.

---

### Post by comthre3 on 2010-10-11
bump!

---

### Post by honestabeinator on 2010-10-11
Same problem here

Edit: Tried x11vnc as well, no dice

---

### Post by comthre3 on 2010-10-11
guess no one is interested in this issue, there was a fix i found in the ubuntu notepad, but it was for the beta release and they claimed that they fixed it in the final version. i cannot find that particular page alas.

---

### Post by krunge on 2010-10-11
Are you sure the X server is actually running? (e.g. examine 'ps wwaux' output)

If there is an X server running, try attaching x11vnc to it and attach the full output to this thread.

---

### Post by comthre3 on 2010-10-12
Xserver is running, and still no luck,, so for now the only way to get this running is via another vnc server, can't we do it using the built-in server?
Thanks

---

### Post by splittingdistant on 2010-10-12
Just to add some weight to this request................


Exactly the same thing has happened to my system post 10.10 upgrade.


Win7 system shows "Connection Refused". No messages of any kind on Ubuntu system.


If I look at preference screen for remote desktop it shows:
*Your desktop is only reachable over the local network. Others can access your computer using the address localhost.*


Clicking "localhost" produces the following error:
*There was an error showing the URL "vnc://localhost::5900"*
*Failed to execute child process "evolution" (No such file or directory)*


Prior to the upgrade the prefs screen showed the IP address of my Win7 system as well as 'localhost'


I hope this info is of some use to potential fixers.

---

### Post by alex0815 on 2010-10-12
I´ve got the same problem. There is no possibility too remote-access the 10.10 client (Windows or Ubuntu-machine).

---

### Post by luvshines on 2010-10-12
Did you try connecting with vncviewer ??

I just gave it a try. Though I am not able to connect through RDP client (which I'll try to debug), I was able to connect through xtightvncviewer and vinagre from Linux

Also tried vncviewer from Win XP Pro SP3, it works.

---

### Post by comthre3 on 2010-10-12
Unfirtunatley niether worked for me,

---

### Post by luvshines on 2010-10-12
> **comthre3 said:**
> Unfirtunatley niether worked for me,

Did you try this(vinagre/tightvncview) on the server itself ?

---

### Post by alex0815 on 2010-10-12
The only thing I didn’t try yet, is installing VNC-Server on the 10.10 machine. I tried to connect from Windows 7 (VNC viewer), VM XP SP3 (VNC viewer), Ubuntu, Suse etc. Before 10.10 everything works fine, so VNC-Server can´t be the solution.

---

### Post by luvshines on 2010-10-12
> **alex0815 said:**
> The only thing I didn’t try yet, is installing VNC-Server on the 10.10 machine. I tried to connect from Windows 7 (VNC viewer), VM XP SP3 (VNC viewer), Ubuntu, Suse etc. Before 10.10 everything works fine, so VNC-Server can´t be the solution.

This is kind of weird

Maybe you can check if 5900 port is responding or not on the server:
```
nc -zv localhost 5900
```

If it is, vncviewer on the server itself should work, right ??

You can also check the port reachability from remote machine (I don't know the Windows machine command for nc)

---

### Post by AlexTheStampede on 2010-10-12
> **luvshines said:**
> This is kind of weird

Maybe you can check if 5900 port is responding or not on the server:
```
nc -zv localhost 5900
```

If it is, vncviewer on the server itself should work, right ??

You can also check the port reachability from remote machine (I don't know the Windows machine command for nc)

I'm having the same issue, and this is what i get:
```
~$ nc -zv localhost 5900
nc: connect to localhost port 5900 (tcp) failed: Connection refused
nc: connect to localhost port 5900 (tcp) failed: Connection refused
```
To add more variety, in my case the client is (would be?) an OSX machine.

---

### Post by shanegrant on 2010-10-12
having the same issue...

---

### Post by ryokea on 2010-10-12
Have the same problem, but found out something interesting. I went in and removed all the checkmarks in all the boxes then enabled the top two and the one for the password. Remote Desktop now works and nc even says 5900 is accepting connections. It seems the UPNP portion of the vnc server is having issues.

---

### Post by honestabeinator on 2010-10-12
I did what ryokea said and it worked. It seems the problem is created by ticking the "Configure network to automatically accept connection" box. Everything works great until that box is ticked and then the machine becomes inaccessible.

So, to fix it, untick all boxes, then tick the top two.

---

### Post by luvshines on 2010-10-13
> **ryokea said:**
> Have the same problem, but found out something interesting. I went in and removed all the checkmarks in all the boxes then enabled the top two and the one for the password. Remote Desktop now works and nc even says 5900 is accepting connections. It seems the UPNP portion of the vnc server is having issues.

If clicking 'configure network...' don't allow Remote desktop to connect, can it be that UpNP support from router is disabled ??

Did you give it a try on the server itself instead of remote machine, with that tick marked ??

Just to be sure, when you allow connections, see if server is listening on 5900 or not:
```
netstat -an | grep 5900
```

---

### Post by alex0815 on 2010-10-13
```

nc -zv localhost 5900
nc: connect to localhost port 5900 (tcp) failed: Connection refused
nc: connect to localhost port 5900 (tcp) failed: Connection refused

```

OK, ryokea´s proposal works. I had to uncheck all boxes and close the window, then I had to leave a password. Now you can read that you can connect your machine over the ip and its name, before you can read that you can connect over localhost. 

```

Connection to localhost 5900 port [tcp/*] succeeded!
alex@ubuntu:~$ netstat -an | grep 5900
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     
tcp        0      0 192.168.0.105:5900      192.168.0.100:49395     
tcp6       0      0 :::5900                 :::*                    LISTEN     

```

---

### Post by splittingdistant on 2010-10-13
ryokea's workaround fixed it for me also.

I no longer have to juggle keyboards & mice!

Many thanks to all, especially ryokea.

---

### Post by comthre3 on 2010-10-13
So i unchecked all the checkboxes, closed it, reopened Remote Desktop, enabled the first two, and the password. still showing localhost. It doesnt seem that this solution fixed it,, shouldnt there be a patch or something?

---

### Post by AlexTheStampede on 2010-10-13
Awesome, ryokea's workaround actually works! And it also seems it still announces itself on the lan, truly beautiful.

---

### Post by luvshines on 2010-10-13
> **comthre3 said:**
> So i unchecked all the checkboxes, closed it, reopened Remote Desktop, enabled the first two, and the password. still showing localhost. It doesnt seem that this solution fixed it,, shouldnt there be a patch or something?

After you have done this, see if the port 5900 is listening or not (use the netstat command mentioned in above comments)

If it is, then try to connect it using vinagre from the server itself

If that works, then from the remote machine see if the 5900 port of the server is reachable:
```
nc -zv <server-ip> 5900 ## Assuming remote machine is Linux
```

If it is then try connecting with vncviewer. If it is not, just check that server is not having any firewalls which are blocking

---

### Post by ryokea on 2010-10-13
> **luvshines said:**
> If clicking 'configure network...' don't allow Remote desktop to connect, can it be that UpNP support from router is disabled ??

Did you give it a try on the server itself instead of remote machine, with that tick marked ??

Just to be sure, when you allow connections, see if server is listening on 5900 or not:
```
netstat -an | grep 5900
```

I know my router is set up for UPNP correctly. Any other computer on the network runs UPNP just fine with it and to the best of my knowledge only the VNC server is having issues.

I tested out my solution using a N810 to connect to my laptop and control it with vncviewer. Actually used that VNC session to make my initial post in this thread as a test.

Here, just for anyone else to look at. Here is with the box unticked
```
james@shade:~$ netstat -an | grep 5900
tcp        0      0 0.0.0.0:5900            0.0.0.0:*               LISTEN     
tcp6       0      0 :::5900                 :::*                    LISTEN
```

And here is what shows up for me after ticking the box
```
james@shade:~$ netstat -an | grep 5900
tcp        0      0 192.168.2.104:10041     88.15.187.173:5900      TIME_WAIT
```

---

### Post by comthre3 on 2010-10-13
> **ryokea said:**
> Have the same problem, but found out something interesting. I went in and removed all the checkmarks in all the boxes then enabled the top two and the one for the password. Remote Desktop now works and nc even says 5900 is accepting connections. It seems the UPNP portion of the vnc server is having issues.

my bad,, It seemed like it worked, ryokea, thanks a lot. would you mind if I put your post in the first post and mark it as solved?

---

### Post by ryokea on 2010-10-13
> **comthre3 said:**
> my bad,, It seemed like it worked, ryokea, thanks a lot. would you mind if I put your post in the first post and mark it as solved?

Sure, go for it.

---

### Post by alex0815 on 2010-10-14
I´m sure it´s not solved, because it´s not working like before, it´s not working without password!

---

### Post by ryokea on 2010-10-14
> **alex0815 said:**
> I´m sure it´s not solved, because it´s not working like before, it´s not working without password!
Mine works with and without a password enabled. Just used it to post this and the password tick box is unchecked.

---

### Post by albertcolin on 2010-10-14
Hello,
         Just re-install vinagre i.e. Vino from Synaptic package manager and then try or else you can use x11vnc also .....

---

### Post by alex0815 on 2010-10-14
Ok, I´ve unticked the passwordbox and it works. Sorry, it was my fault. Thanks!

---

### Post by muayed on 2010-10-15
Hi, I had the same problem, it works absolutely fine now from windows 7, thanks.

---

### Post by psychydyl on 2010-10-22
1. Run vino-preferences (System>Preferences>Remote Desktop)

The hype-box below the 2nd option says blah blah blah ... localhost..
This ought to be your IP or your <hostname.domain> (e.g., macsaur.local  or starduck.local or laura.lassoon or whaterver yours is. Check /etc/hostname. It'll just have your hostname. Your domain, also called 'workgroup' is found in /etc/samba/smb.conf).


2. Untick all options.

3. Quit vino-preferences (<=>Remote Desktop).

4. Relaunch vino-preferences (System>Preferences>Remote Desktop).

5. Tickmark your choices EXCEPT for the "Configure network automatically to accept connections" option. Its this option, when ticked, fraks up the remote desktop connection. Check for yourself by ticking it (and then going back to step 2 to fix it).

The hype box should now be showing your hostname and IP instead of "localhost".

6. Ta-da!

---

### Post by deschmit on 2010-12-22
I follow all the directions given by psychydyl and it still says

Your desktop is only reachable over the local network. Others can access your computer using the address localhost.

Any other ideas?

$ dpkg-query -l vino
gives
ii  vino           2.32.0-0ubuntu VNC server for GNOME

---

### Post by gitana on 2011-01-21
I just started using Ubuntu last month, and had the UPnP option enabled and working up until a couple days ago when I couldn't access the computer remotely any more.  Today I found this thread, and unchecking the UPnP option worked for me (at least according to netstat - haven't had a chance to test remotely), but I'm not sure why it was working but now isn't.  Is there some way to fix the issue without disabling UPnP?  My choices on the router are to forward one single path, meaning if the path changes I'm SOL until I can get at it locally to change it, or to use UPnP.

---

### Post by antonius on 2011-02-22
On mine, it's working for some users, my kids user acc't, my brother, but not mine....????

any ideas?

---

### Post by wgbuntu on 2011-02-26
Same ip problem here. New install of 10.10 amd64. Followed all the suggestions in this thread. Port 5900 is open and listening but still shows ip address as localhost. I can use ssh to access remote computer. I can connect to server. I cannot use vinagre on localhost to connect to vino. Weird thing, when I click on the localhost link in remote desktop preferences it brings up the evolution program. Any more help?

---

### Post by isildur100 on 2011-03-24
I have the same problem and the workarounds stated in this thread did not work for me...

When I click on the localhost link (where my IP should be) I get an error because I don't have evolution installed.

Does anyone have this working in ubuntu 10.10 amd64 ?

---

### Post by TekNullOG on 2011-03-27
> **isildur100 said:**
> I have the same problem and the workarounds stated in this thread did not work for me...

When I click on the localhost link (where my IP should be) I get an error because I don't have evolution installed.

Does anyone have this working in ubuntu 10.10 amd64 ?

I have the exact same problem. Ubuntu amd64 not working. I tried all the solutions mentioned here and nothing worked.

Really annoying.

---

### Post by Mononofu on 2011-03-30
Doesn't work for me either.

However, it does work on another Ubuntu 10.10 box I have. :confused:

edit: decided to use x11vnc, works perfectly: [https://help.ubuntu.com/community/VNC/Servers#x11vnc](https://help.ubuntu.com/community/VNC/Servers#x11vnc)

---

### Post by alphalux on 2011-04-07
This, in my case, appears to be due to me recently adding a second X screen for dual monitor support. I have found this referenced below.

Thread: [http://ubuntuforums.org/showthread.php?t=1603059](http://ubuntuforums.org/showthread.php?t=1603059)
Bug Report: [https://bugs.launchpad.net/ubuntu/+source/vino/+bug/682578](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/682578)

Apparently, vino is attempting to open two X screen servers using the same port. I hope this helps others watch this bug / thread to find a fix. Any practical workaround info would be appreciated.

---

### Post by deckoff on 2011-04-17
What helped me was to remove vino-preferences in synaptic, and download and install the verstion from 10.04, which works fine for me( downgraded.
[http://pkgs.org/download/ubuntu-10.04/ubuntu-main-i386/vino_2.28.2-0ubuntu2_i386.deb.html](http://pkgs.org/download/ubuntu-10.04/ubuntu-main-i386/vino_2.28.2-0ubuntu2_i386.deb.html)

THIS IS THE LINK. Keep fingers crossed for West HAm United, if this worked for you :)

---

### Post by Vronth on 2011-10-19
The ryokea solution worked for me too.
In october 2011 after an upgrade to Oneiric 11.10 
 
Force the firewall to open the 5900 port.
-------------------------------------------------
sudo ufw enable
sudo ufw allow 5900
 
Then force the Remote Server to re-save the config settings.
----------------------------------------------------------------------
Uncheck all the boxes in the Remote Server dialogue box. 
Close the dialogue box. 
Reopen the dialogue box.
Check the top two.
Check the pasword box if needed.
Retype the password, just in case.
Close the dialogue box. 
Reconnect from client.
 
That's what worked for me. Thanks ryokea.

---

