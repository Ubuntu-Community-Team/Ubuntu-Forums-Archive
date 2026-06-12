---
title: "mythfilldatabase - not automatically updating"
date: 2008-01-20
forum: Mythbuntu
---

### Post by daleq on 2008-01-20
Hi,

I'm running Mythbuntu 7.10 and amazed at how well it all works.

One minor issue is that, even though I have, "Automatically run mythfilldatabase" checked, no updates seem to occur.

I don't see any entries in the crontab.  Does this get set some other way?

Should I just add /usr/sbin/mythfilldatabase to my myth user's crontab?  If so, is there anything else that needs to be stopped prior to running mythfilldatabase?

Thanks for any help.
Dale

---

### Post by newlinux on 2008-01-20
Maybe there is an error with it. When you run it manually do you get any updates? Have you checked the status screen in the Information Center to see if there are any errors with the grab?

---

### Post by jakemonO on 2008-01-20
I have the same problem. I can run mythfilldatabase just fine manually and the status screen doesn't indicate anything is wrong...

---

### Post by superm1 on 2008-01-21
In your frontend, there is an option for automatically running mythfilldatabase.  It's under the general section if i'm remembering correctly.

---

### Post by daleq on 2008-01-21
Thanks for the replies newlinux, jakemon0, and superm1.

newlinux, your suggestion got me on the right track.

When I looked in the log file /var/log/mythtv/mythbackend.log.1, I saw;

	2008-01-21 01:19:36.379 Running mythfilldatabase
	sh: cannot create /var/log/mythfilldatabase: Permission denied

When I was filling in the edit fields on the frontend GUI, I just picked a log name (/var/log/mythfilldatabase) that seemed reasonable.

I'm attempting to resolve this problem by changing the log file to;
/var/log/mythtv/mythfilldatabase

The /var/log/mythtv directory is owned by the mythtv user, so there should be no permission problems.

If I don't re-post, this worked for me.  :)

Thanks again for the replies.
Dale

---

### Post by daleq on 2008-01-22
FYI

Changing the log file to /var/log/mythtv/mythfilldatabase resolved this issue for me.

Thanks again for the pointers.

---

### Post by brenthaag on 2008-05-14
> **superm1 said:**
> In your frontend, there is an option for automatically running mythfilldatabase.  It's under the general section if i'm remembering correctly.

I ran into this situation today, after realizing that my listings hadn't been updated since I installed Mythbuntu last Friday.

Just curious...shouldn't this be enabled by default?

OT: I was just impressed with how easy it was to install.  I had KnoppMyth before, but this was so much nicer and things just worked.

---

### Post by asathoor on 2008-06-04
I have the same problem, and tried to place the logfile in /var/log/mythtv/mythfilldatabase.log

Then I found this:

---

per@Horus:/var/log/mythtv$ less mythfilldatabase.log | grep run
config file /home/mythtv/.mythtv/DanskeKanalerXmlTV.xmltv does not exist, run me with --configure

---

So the xmltv-file should be in the directory /home/mythtv/.mythtv/....xmltv

---

### Post by asathoor on 2008-06-10
I tried another solution:

1. Turn off the automatic update in mythfrontend. 
2. Since my pc is turned off and on I use anacrontab for updates, therefore:
3. sudo gedit /etc/anacrontab
4. Add this line:

1       60      mythtvProgramlisteOpdateret     /usr/bin/mythfilldatabase --update --max-days 7 --mark-repeats

5. Save

Now you can test the settings, do something like this:

# anacrontab -f -n

After this it worked at my system... :popcorn:

---

