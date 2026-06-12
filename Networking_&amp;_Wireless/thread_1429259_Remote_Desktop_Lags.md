---
title: "Remote Desktop Lags"
date: 2010-03-13
forum: Networking &amp; Wireless
---

### Post by derekeverett on 2010-03-13
I work at home and require a constant Remote Desktop connection to a windows machine at work.

I find the default Remote Desktop application that ships with Ubuntu to lag quite a bit, especially compared to the win7 Remote Desktop.

Win7 has settings that allow me to specify that I have a broadband internet connection, which sped things up quite a bit for me. I can't seem to find any such preference setting in Ubuntu, do such settings exist that I am not aware of?

Is there perhaps another Remote Desktop application that works better that I should be looking at.

I would love to work in Ubuntu more often but I need to resolve this issue first. I find myself in Windows most of the night as the Remote Desktop is literally twice as responsive.

---

### Post by derekeverett on 2010-03-19
Bump.

I think at this point I'm looking for another application that has some better connection options...

---

### Post by Dustout on 2010-03-22
I have had a similar experience with the default Ubuntu remote desktop, sometimes it feels like a powerpoint presentation lol. I have found that using GRDC Remote Desktop Client to be much more responsive.

Also if you are doing this at work then you might find it handy to use SSH -X [username]@[ipaddress] to access your ubuntu box, because with that setup you could make it look less like you are remoting in and more like you are doing your work :P

---

### Post by jrssystemsnet on 2010-03-22
> **derekeverett said:**
> Bump.

I think at this point I'm looking for another application that has some better connection options...Use the Terminal Server Client.  If things are still slow/laggy, try going to the Display tab and setting color depth to 256 colors (this only takes effect in between sessions, so you'll need to log out and back in again for changing it to make a difference).

The "Remote Desktop Viewer" sucks something fierce; I can't for the life of me understand why it was added in when the Terminal Server Client was already there and works considerably better for, well... everything.

---

### Post by derekeverett on 2010-03-22
> **Dustout said:**
> I have had a similar experience with the default Ubuntu remote desktop, sometimes it feels like a powerpoint presentation lol. I have found that using GRDC Remote Desktop Client to be much more responsive.


GRDC - Thank you for the suggestion I will try it. However, I have improved the performance of the default client significantly by changing to 256 colors.

---

### Post by derekeverett on 2010-03-22
> **jrssystemsnet said:**
> Use the Terminal Server Client.  If things are still slow/laggy, try going to the Display tab and setting color depth to 256 colors (this only takes effect in between sessions, so you'll need to log out and back in again for changing it to make a difference).

The "Remote Desktop Viewer" sucks something fierce; I can't for the life of me understand why it was added in when the Terminal Server Client was already there and works considerably better for, well... everything.

Changing to 256 colors has helped a great deal. Thank you!

---

### Post by Dustout on 2010-03-23
> **jrssystemsnet said:**
> Use the Terminal Server Client.  If things are still slow/laggy, try going to the Display tab and setting color depth to 256 colors (this only takes effect in between sessions, so you'll need to log out and back in again for changing it to make a difference).

The "Remote Desktop Viewer" sucks something fierce; I can't for the life of me understand why it was added in when the Terminal Server Client was already there and works considerably better for, well... everything.
I have always been a sucker for defaults, "Terminal Server Client" is my new favorite thing, i cannot believe i haven't seen it until now. Thank you jrssystemsnet :p

---

### Post by Dysan911 on 2010-10-31
Bringing this old post back to life.   I don't think lowering the colors would really RESOLVE this issue.     Thats kind of a trade off.    Why should you lower the colors when the Win7 or XP RDP clients can RDP to other Window systems with full colors and work just perfectly?      As superior Ubuntu is in ways it can't manage to connect via RDP without lagging,  pausing, mouse freezing every 30-45 secs?  

I have searched and googled the issue and there seems to be no resolution to this.     Doesn't ANYONE know why it does that?    

Very frustrating and I was hoping the latest version of Ubuntu would take care of that problem but its still there.

---

### Post by derekeverett on 2010-10-31
> **Dysan911 said:**
>  

Very frustrating and I was hoping the latest version of Ubuntu would take care of that problem but its still there.

It is very frustrating.. unfortunately I have given up on using Ubuntu for the most part.. largely due to the fact that I rely on RDP for 40-60 hours every week and it just doesn't cut it.

I would love to begin using Ubuntu regularly again, but that won't happen until this issue is resolved by the good developers here or until I no longer rely on RDP.

The biggest issue I had with the Remote Desktop was the crashing. I was tolerating the lags.. and I had my color settings etc. as low as I could get them, but the RDP would just crash altogether often and I just couldn't have it.

---

### Post by jrssystemsnet on 2010-10-31
> **derekeverett said:**
> The biggest issue I had with the Remote Desktop was the crashing. I was tolerating the lags.. and I had my color settings etc. as low as I could get them, but the RDP would just crash altogether often and I just couldn't have it.

I dunno what to tell you, other than that I don't share your problem.  The TS Client in Ubuntu works, for me, exactly the same as Windows' RDP client does.  No better, no worse.

---

### Post by Dysan911 on 2010-10-31
> **jrssystemsnet said:**
> I dunno what to tell you, other than that I don't share your problem.  The TS Client in Ubuntu works, for me, exactly the same as Windows' RDP client does.  No better, no worse.


JR,

Wish I could say the same.   I have tried various Ubuntu distributions over the years and connecting via wireless over my home network,  I cannot seem to get the same performance on RDP as I can with a Windows client.      I thought at first maybe its just the RDP client that comes with Ubuntu and that I can download a more robust better version but I was surprised to find that there really isn't alot of offersings in that regard.   

Anyhow,  the symptoms are always the same,   The amount of lag is noticeable but at first its tolerable and then within a few mins the mouse and keyboard will no longer respond for about 15 to 20 secs and then it will resume again for a few more mins and then the pause / freeze again.      Ughh So frustrating.     

The amount of times I use Rdp,  It got to the point where I had to abandon Ubuntu and hope that maybe the next release would be better but it never is.  

Really wish there was a fix.

---

### Post by derekeverett on 2010-10-31
> **Dysan911 said:**
> JR,

The amount of times I use Rdp,  It got to the point where I had to abandon Ubuntu and hope that maybe the next release would be better but it never is.  

Really wish there was a fix.

Yup +1

---

### Post by jrssystemsnet on 2010-10-31
Video card problems maybe?  Or wireless problems?

I wish I knew what to tell you; like I said, I haven't had any issues whatsoever with the TS Client on my workstations or my netbooks.  I use them on a daily basis to connect with Windows machines and occasionally with other Ubuntu machines running xRDP.

---

### Post by jrssystemsnet on 2010-11-18
> **Dysan911 said:**
> The amount of times I use Rdp,  It got to the point where I had to abandon Ubuntu and hope that maybe the next release would be better but it never is.  

Really wish there was a fix.

OK, today for the first time I really encountered the same problems you were having - the user had some kind of "desktop wallpaper switcher" thing that was making my life a living hell, because it was rearranging icons (to the same place) every second, which was triggering events across the RDP connection, and making my life a living hell.

Luckily, I also found the solution:

```

me@box:~$ apt-get update && sudo apt-get install remmina remmina-gnome

```

Remmina.  You'll find it in Applications->Internet after installing it as above.  It's BLINDING fast... and, thank Ghu, hides the wallpaper on the remote machine by default, among other things.  Like TS Client, it supports RDP, RDPv5, VNC, and a couple other things.  Unlike TS Client, it's fast as hell. :) :) :)

---

### Post by datman on 2010-12-22
Hey that's awesome, no more RDP lag, thanks for the tip!

---

### Post by coilwinder on 2010-12-27
Here is another thing that might help more than changing the color depth for the Remote Desktop Viewer. Though probably not better than the alternatives posted above (I haven't tried them), I just thought I could add this anyway.

Open terminal, issue the command:

gconf-editor

Then navigate to: desktop / gnome / remote_access. Enable the "disable_xdamage" setting.


I found the solution here: [http://start.ubuntuforums.org/showthread.php?p=9659063](http://start.ubuntuforums.org/showthread.php?p=9659063)

---

