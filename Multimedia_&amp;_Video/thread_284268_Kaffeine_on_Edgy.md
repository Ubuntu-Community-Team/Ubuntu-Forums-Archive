---
title: "Kaffeine on Edgy"
date: 2006-10-25
forum: Multimedia &amp; Video
---

### Post by TorchlightJay on 2006-10-25
So I updated both of my computers to edgy recently and kaffeine worked for a day or so and now it won't open. I click the icon, it bounces but kaffeine doesn't open. I've tried reinstalling it, --purge removing it then installing it and installing it from source but nothing. Any ideas as to what's going on with my kaffeine?

---

### Post by Antonlacon on 2006-10-25
Launch from a terminal and read output.

---

### Post by TorchlightJay on 2006-10-25
Strange thing, I don't get an output. It pauses for a second and then goes back to the way it was. Something like

user@comp:~$kaffeine %U
user@comp:~$

same if I type just kaffeine. It's the weirdest thing. It never happened with Dapper but is happening now with the Edgy upgrade on both of my computers. It's weird

---

### Post by dik666 on 2006-10-26
I just did a clean install of edgy (kubuntu) and the same thing happened to me.  The first time I ran kaffeine it worked fine.  I then installed the nvidia driver for my graphics card and rebooted.  Now kaffeine just gives me the bouncing icon.  If I run it from a terminal I don't get any output at all.  ](*,)

---

### Post by chudder on 2006-10-27
I'm having similar problems too but I haven't upgraded to Edgy yet.  I'm still on Dapper.  I was streaming and then i found an old .swf file and I think it was intended to only be run on windows and just as I was about to run it on wine my computer on its own reset.  I can't explain it and now Kaffiene doesn't work.  I have completely removed and reinstalled but to no avail.  Could someone please help.  Thanx](*,)

---

### Post by dik666 on 2006-10-27
I discovered the problem with my system and was able to fix it.  There was a zombie kaffeine process running even after rebooting.  After I killed it everything went back to working normally.  The process was there even after rebooting so it must be part of the session restore or something.  Just do a "ps -ax | grep kaffeine" to see if you have the same thing.  :cool:

---

### Post by chudder on 2006-10-27
When I stream video it's not as much of a problem but when I do audio it is.  I see it initializing some keui server or something and then there are two processes of Kaffeine.  I'm not sure why this is.  Any ideas?

---

### Post by ardnut on 2006-10-30
> **dik666 said:**
> I discovered the problem with my system and was able to fix it.  There was a zombie kaffeine process running even after rebooting.  After I killed it everything went back to working normally.  The process was there even after rebooting so it must be part of the session restore or something.  Just do a "ps -ax | grep kaffeine" to see if you have the same thing.  :cool:

I have the exact same problem, I like to have kaffeine set to load in the kde task tray but this causes some zombie kaffeine process on every boot.  I've currently got a 1 line script which runs on each boot to kill kaffeine but that's an ugly fix.

Any idea whats causing this problem?

---

### Post by TorchlightJay on 2006-10-30
Ya, i solved it with mine. Just go to KsysGuard and close kaffeine. For some reason, it will keep running even if you reboot your computer. If this is happening, you can't open kaffeine. Open KSysGuard (Ctrl + Esc) and close the instance of kaffeine. After that it should work.

---

