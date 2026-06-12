---
title: "VNC authentication failed"
date: 2007-11-26
forum: Mythbuntu
---

### Post by aznewsh on 2007-11-26
I have enabled VNC via the control panel and it stays enabled, I set a password, (more than once), I also tried via vncpasswd from command line. Everytime I try to connect remotely from another ubuntu box using remote desktop connection and the following: vnc:/192.168.2.7:5900 I get a password prompt, after which I enter my password which I know is correct and it comes back authentication failed. Connection aborted.

I do not get the no server running at this address error so the remote connection is seeing the server, it is just unable to authenticate???

Where should I start troubleshooting this?

Just to add I have restarted X and even rebooted for good measure

---

### Post by road2elysium on 2007-11-26
Are you using the Mythbuntu 7.10 release?  I vaguely recall using an alpha release where I had VNC issues a while back.

---

### Post by superm1 on 2007-11-26
Yes there was a bug all the way up through the release candidate that you couldn't change the password.  It was fixed on the final disk.

---

### Post by aznewsh on 2007-11-27
> **road2elysium said:**
> Are you using the Mythbuntu 7.10 release?  I vaguely recall using an alpha release where I had VNC issues a while back.

Yes I downloaded the iso in the last week, I am pretty sure it is though I am not sure how to check for sure

---

### Post by superm1 on 2007-11-27
> **aznewsh said:**
> Yes I downloaded the iso in the last week, I am pretty sure it is though I am not sure how to check for sure

For this particular bug, the easiest way to check would be to check the version of the control centre:

```
dpkg -l | grep control-centre
```

You should have been offered to upgrade it though if for some reason you ended up with an older ISO.

---

### Post by aznewsh on 2007-11-27
> **superm1 said:**
> For this particular bug, the easiest way to check would be to check the version of the control centre:

```
dpkg -l | grep control-centre
```

You should have been offered to upgrade it though if for some reason you ended up with an older ISO.

Here is the response to that command - not totally sure I understand it:

$ dpkg -l | grep control-centre
ii  mythbuntu-control-centre                   0.11-0ubuntu1~ppa1                        Mythbuntu Configuration Application

---

### Post by superm1 on 2007-11-27
> **aznewsh said:**
> Here is the response to that command - not totally sure I understand it:

$ dpkg -l | grep control-centre
ii  mythbuntu-control-centre                   0.11-0ubuntu1~ppa1                        Mythbuntu Configuration Application

You do have the final release then. Try connecting with a different client If you can.

---

### Post by aznewsh on 2007-11-27
> **superm1 said:**
> You do have the final release then. Try connecting with a different client If you can.

I did that already, I tried two different clients from my Kubuntu box (KRDC and Terminal server client) and tightvnc from my windows XP box

---

### Post by Danikar on 2007-11-27
I am having this same issue, but with just Ubuntu.

If I turn password off I can connect no problem.  But if I set the password it wont authenticate, no matter how many times I reset it.

---

### Post by aznewsh on 2007-11-27
> **Danikar said:**
> I am having this same issue, but with just Ubuntu.

If I turn password off I can connect no problem.  But if I set the password it wont authenticate, no matter how many times I reset it.

I am not sure how to turn the password off in mythubuntu 

This is starting to sound like a bug, are any developers watching this thread?

---

### Post by Danikar on 2007-11-27
Interesting, I took the number out of my password and it seems to work now.

I am going to do more testing.

Edit: Ok my problem is probably different.

Ubuntu seems to have a password length limit on it.  My password is 9 characters long, it only allows 8 characters.  Which is interesting. (This was my problem)

Also, i noticed, if u have a old password selected and u start to type over it, instead of deleteing the current password and typing the first letter, it just deletes the password and does nothing, so u must retype the first letter.  I don't belive this was my problem, but it is somthing i noticed.

---

### Post by superm1 on 2007-11-27
> **aznewsh said:**
> I am not sure how to turn the password off in mythubuntu 

This is starting to sound like a bug, are any developers watching this thread?

I am. It is not possible to have "no" password for vnc. If we start going down the list of areas that things can to wrong:

Post your xorg.conf. We will make sure that it is pointing to the right place for your password.

Make sure the passwordfile exists in /root/.vnc

Don't use any other vnc servers including but not limited to x11vnc and vino.

---

### Post by superm1 on 2007-11-27
> **Danikar said:**
> Interesting, I took the number out of my password and it seems to work now.

I am going to do more testing.

Edit: Ok my problem is probably different.

Ubuntu seems to have a password length limit on it.  My password is 9 characters long, it only allows 8 characters.  Which is interesting. (This was my problem)

Also, i noticed, if u have a old password selected and u start to type over it, instead of deleteing the current password and typing the first letter, it just deletes the password and does nothing, so u must retype the first letter.  I don't belive this was my problem, but it is somthing i noticed.

Can you please file a bug against vnc4server?

My understanding was that only the first 8 characters are used with the rest diagarded, but this may be incorrect or have changed.

---

### Post by csaga on 2007-11-27
It happened to me exactly this problem, "VNC authentication failed" and when I uncheck the box and dont set password the remote connection is work! I used a password with 8 characters.
What is wrong?
(I have a Windows system, with VNC Viewer and connect remotely to Ubuntu 7.04 system)

---

### Post by superm1 on 2007-11-27
> **csaga said:**
> It happened to me exactly this problem, "VNC authentication failed" and when I uncheck the box and dont set password the remote connection is work! I used a password with 8 characters.
What is wrong?
(I have a Windows system, with VNC Viewer and connect remotely to Ubuntu 7.04 system)
Mythbuntu is not available on Ubuntu 7.04.

---

### Post by aznewsh on 2007-11-27
> **superm1 said:**
> I am. It is not possible to have "no" password for vnc. If we start going down the list of areas that things can to wrong:

Post your xorg.conf. We will make sure that it is pointing to the right place for your password.

Make sure the passwordfile exists in /root/.vnc

Don't use any other vnc servers including but not limited to x11vnc and vino.

I don't want to run with no password.

here is the relevant part of my xorg:

Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5500]"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	Option		"SecurityTypes"	"VncAuth"
	Option		"UserPasswdVerifier"	"VncAuth"
	Option		"PasswordFile"	"/root/.vnc/passwd"
EndSection

Yes the password file does exist in /root/.vnc/

No I have not installed any other vnc servers

---

### Post by superm1 on 2007-11-27
> **aznewsh said:**
> I don't want to run with no password.

here is the relevant part of my xorg:

Section "Screen"
    Identifier    "Default Screen"
    Device        "nVidia Corporation NV34 [GeForce FX 5500]"
    Monitor        "Generic Monitor"
    Defaultdepth    24
    Option        "SecurityTypes"    "VncAuth"
    Option        "UserPasswdVerifier"    "VncAuth"
    Option        "PasswordFile"    "/root/.vnc/passwd"
EndSection

Yes the password file does exist in /root/.vnc/

No I have not installed any other vnc servers
Then make sure the length of the password is 8 characters as reported by the other poster above.

---

### Post by Cryophallion on 2007-11-27
I ran into this today also.

Last night I had no problem connecting via vnc to my myth box from my laptop, using the local ip.

So, last night I set my router to forward port 5900 to the myth box, in the hopes of running some tweaks today (since we all know how long a fill can take). I got in, tried to connect (using both the laptop and my office xp machine with vncviewer), and I got the auth problem.

My password is 8 characters exactly. I will test again when I get home to see if I can connect locally again. 

I get to the box, I just can't get the password to be accepted. I saw something about display:1 earlier today, but that didn't work either. I'll let you know if it is just a remote problem or if it persists to the local network too.

Note: I just noticed that vnc is under monitor on the xorg.conf above. I switched from dvi-hdmi to svga cables this morning (svga comes out clearer on my tv, and I can choose whether to under or overscan, though unfortunately not perfect scan). If that is what caused this, then that is one weird side effect of switching monitor types.

---

### Post by Cryophallion on 2007-11-27
Ok, so I am now at home. It doesn't work here either.

I have:
1. tried setting the password through mythcenter
2. tried running vncpasswd as myself
3. tried running vncpasswd under sudo
4. checked to see if the file is under /root/.vnc (and it is)
5. uninstalled through mythcenter and re-installed
6. turned off cd rom in sources (in case the cd rom had an old package) and reinstalled.
7. tried logging on using outside network
8. tried logging on using inside network

And nothing seems to work. Any ideas would be appreciated.

---

### Post by aznewsh on 2007-11-27
> **superm1 said:**
> Then make sure the length of the password is 8 characters as reported by the other poster above.

Password was 6 - changed to 8, restarted x and tried again - no difference

I need vnc to complete my system - help

---

### Post by Cryophallion on 2007-11-28
I gave up on vnc4server this morning, and installed vino through synaptic. I ran vino-preferences (which has to be done in an x environment as it is a graphical display), and restarted x. Then I ran vino-session, and I was able to get in no problem. Then I added vino-session to the autostarted programs in settings, and now I'm all set.

I use vino all the time in my standard ubuntu desktop, and I see no reason not to use it here. I am not sure of the benefits of vnc4server, but as it isn't working, even if there is a slight memory footprint difference, it doesn't matter. 

Hope this works for you too aznewsh. I know this doesn't fix the underlying problem, but it is at least a temporary fix.

---

### Post by aznewsh on 2007-11-28
Thanks this does work for me and I will use this fix.

There is however one small caveat, I noticed that if the mythtv gui was on the screen when I was controlling and I used the up and down arrows to cycle through options, it did actually cycle on the myth machine display but on the remote session display it showed no change??

This is not a big deal since I doubt I will have much cause to do anything there remotely, but it would be nice to have full functionality

---

### Post by aznewsh on 2007-11-28
Actually it seems worse than that, the vnc session seems unable to render the myth display at all, if i close myth frontend and then restart it, the graphical display never completes on the remote session, I see the correct background but no content.

---

### Post by superm1 on 2007-11-28
This is because you can't render opengl in vnc.  You can hit "Refresh Screen" In you VNC client to refresh it, but it won't happen live.

---

### Post by dannyboy79 on 2007-11-28
i use x11vnc. I only have my ssh port open on my home ubuntu box. then I ssh in, create a tunnel, then start up x11vnc --usepwd. then i minimize putty, then I use tightvncviewer for windows xp and I can access my ubuntu box and then start up mythtv frontend.  this is from work too!! I do notice issues, like for example, when at the first window, I see all my choices but when I try to arrow over to the right or left, the little highlighted circle doesn't change to the one it should, but if I hit enter, it enters that option. this may be because I am using the opengl theme I believe. my point was that x11vnc tunnelled thru ssh is great along with tightvncviewer.

---

### Post by aznewsh on 2007-11-28
That makes sense - I can live with that.

I have found a solution but it is only really a workaround, there does seem to be a bug that needs addressing

Thanks to everybody for their input, I hope as I get this setup more figured out I will be able to give back more too

---

### Post by Cryophallion on 2007-11-28
Aznewsh:

Just a thought - why is vino so integral for you? For me, it is only for setup reasons and so my wife can watch tv while I tweak run mythfilldatabase for the zillionth time to try to get the hd channels to sort properly (which seems to be somehting that may be fixed for .21... so hopefully happening soon).

However, for scheduling the recordings and basic myth checkups - try out mythweb. I hadn't tried it until today, but it is great for remote checkups and scheduling. Plus, for such things as changing channel #s, you don't need to re-run  fill. So, big plus for me.

Anyway, try out mythweb. Be aware of the bug with the mysql access, which has an easy solution on the forum. Hopefully this will let you do what you want without needed to vnc too much. 

I didn't have too many problems with vnc redraw, although it took a little while at first, it did speed up. However, using the arrow keys in windows would move the bottom scrollbar (since my desktop is less than 1280 wide), so I ended up using linux on my laptop at work.

Best of luck.

---

### Post by dannyboy79 on 2007-11-29
> **Cryophallion said:**
> Be aware of the bug with the mysql access, which has an easy solution on the forum.  

can you please elaborate on this. I use mythweb a lot. Also, I was wondering if anyone can help with an issue I am having with mythweb and accessing recordings that are stored on my slave be/fe. the thread is here: [http://ubuntuforums.org/showthread.php?t=573759](http://ubuntuforums.org/showthread.php?t=573759)

---

### Post by Cryophallion on 2007-12-01
> **dannyboy79 said:**
> can you please elaborate on this. I use mythweb a lot. Also, I was wondering if anyone can help with an issue I am having with mythweb and accessing recordings that are stored on my slave be/fe. the thread is here: [http://ubuntuforums.org/showthread.php?t=573759](http://ubuntuforums.org/showthread.php?t=573759)

I was referring to the issue with the database password no matching the password in the mythweb settings. This causes you to not be able to access the database. If you're in already, you're golden.

---

### Post by kubug on 2007-12-08
HI All, 
I just read over this thread and just like you all I couldn't connect to the remote server over VNC. 

This had been bugging me for days. I tried changing the password, but nothing worked.

Today, as I looked over this thread one of you mentioned that when he entered the password over the old one, it didn't really erase the old one (it seemed to only remove the *stars*). 

So what I did was hold down the backspace button (erase) for 15 seconds and pushed it some more to make sure there was NOTHING in the line.

Then I reentered the password and BINGO. It worked. 

Could this be the problem?? That when you enter the password wrong, and you want to retype it, it doesn't actually erase the old one??

---

### Post by srudes2 on 2008-06-16
wow thanks!!!
SOLUTION to the problem is to just press the backspace button for 15 minutes when entering a new password for the vnc server.
You save me a lot of time thanks!

---

### Post by pimlottc on 2009-02-04
> **kubug said:**
> Today, as I looked over this thread one of you mentioned that when he entered the password over the old one, it didn't really erase the old one (it seemed to only remove the *stars*). 

So what I did was hold down the backspace button (erase) for 15 seconds and pushed it some more to make sure there was NOTHING in the line.

Then I reentered the password and BINGO. It worked. 

Could this be the problem?? That when you enter the password wrong, and you want to retype it, it doesn't actually erase the old one??

Wow, what a ridiculous bug.  This tripped me it too, thanks so much for this post.

Is this bug being tracked/fixed?

---

### Post by sclewis12 on 2009-03-18
AWESOME Kubug!
I cannot believe that bug was not fixed by now.

Either way, thanks for letting us know. I was very upset it did not work.

---

