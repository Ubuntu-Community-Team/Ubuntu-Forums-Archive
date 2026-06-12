---
title: "simplify media and 9.10 karmic"
date: 2009-12-23
forum: Multimedia Software
---

### Post by peedeeramone on 2009-12-23
i just want to know how everyone is working [simplify media]("http://www.simplifymedia.com") in 9.10? rhythmbox wont load the daap or upnp plugin and banshee hasnt ever been able to play simplify tracks. the only way i can get my simplify media tracks is to use xbmc. while a very nice media center, its a little too much when multitasking. (btw does anyone know a hotkey to toggle fullsrceen in xbmc?)

anyway i was just wondering what fixes people have come up with

---

### Post by ergosteur on 2010-01-08
bump on this.

Is there any other player, or a fix?

---

### Post by peedeeramone on 2010-01-08
i believe the site even says it supports rhythmbox in karmic but of course it doesnt.

---

### Post by JohnnieRico on 2010-01-14
It's strange. If you search the simplifymedia support page for "9.10", you'll find the following documentation page: [http://na6.salesforce.com/_ui/selfservice/pkb/PublicKnowledgeSolution/d?orgId=00D80000000MHON&id=50180000000WsYO&retURL=%2Fsol%2Fpublic%2Fsearch.jsp%3Fsearch%3D9.10%26orgId%3D00D80000000MHON&ps=1&pPv=1](http://na6.salesforce.com/_ui/selfservice/pkb/PublicKnowledgeSolution/d?orgId=00D80000000MHON&id=50180000000WsYO&retURL=%2Fsol%2Fpublic%2Fsearch.jsp%3Fsearch%3D9.10%26orgId%3D00D80000000MHON&ps=1&pPv=1)

So it looks like some sort patch is needed for that python script but it's not clear where one can find this patch -- the "installation directory" doesn't have a coherence_patch.sh script.

---

### Post by Loco Ulysses on 2010-01-18
I don't have coherence_patch.sh either, but I followed JohnnieRico's link, and a link there (under 9.10 where it says "**[COLOR=DarkRed]IMPORTANT[/COLOR]**") led me to [this page]("http://coherence.beebits.net/changeset/1473#file0") with a diff file which I have attached. I haven't bothered to write a shell script, but if you just patch /usr/lib/rhythmbox/plugins/upnp_coherence/UpnpSource.py with it everything should be fine, Rhythmbox now lists all my shared songs.

To be more explicit the steps I followed were:

[LIST=1]
[*]Install python coherence ("sudo apt-get install python-coherence")
[LIST]
[*]EDIT: Be sure to enable this in Rhythmbox: Edit > Plugins > DLNA/UPnP
[/LIST]
[*]copy the attached coherence_patch.txt to /usr/lib/rhythmbox/plugins/upnp_coherence/
[LIST]
[*](alternatively save [this file]("http://coherence.beebits.net/changeset/1473?format=diff&new=1473") there as coherence_patch.txt)
[/LIST]
 
[*]go to that directory in a terminal and "sudo patch < coherence_patch.txt"
[/LIST]
If someone else wants to verify, I think we can call this one solved.

---

### Post by joehasmint on 2010-01-19
yeah it worked for me on mint 8

---

### Post by peedeeramone on 2010-01-19
thanks for the hint.

i followed your instructions and reenabled the upnp plugin on rhythmbox and i can now list tracks but i get an error about audiosink. after fiddling with it some more rhythmbox is crashy and doesnt list any simplify devices.

i also tried it with my netbook also running 9.10 and it seemed to work fine, though much slower than i remembered.

so perhaps the first issue is a system-specific one. i will look more into that.

any one else get the audiosink error?


thanks to Loco for getting this to work. hopefully some others will find this. who should we send this to so that it will be fixed for all?

also on a whim, does anyone have simplify working with banshee? i dont really care for rhythmbox...

---

### Post by Loco Ulysses on 2010-01-19
Banshee doesn't seem to have UPnP support yet, that I can find.

I'm none too fond of Rhythmbox myself, currently when I start it up it immediately dies and only on the second start is it okay. It's also pretty clunky with my Simplify shares. Of course who knows if Banshee would do any better. OP said xbmc works, I might try it, I think my work machine could handle it.

---

### Post by peedeeramone on 2010-01-19
xbmc works, you add a upnp source i belive. it doesnt list the directory very quickly but it does work. im sure your computer can run it fine. my netbook can run it along with slideshows, browsers etc running alongside

the biggest problem i have with it is that i dont know of a way to minimize it quickly.

---

### Post by Pork Chop on 2010-01-28
Did you guys get that to work with the simplifymedia supplied daap share script?

Also, does running "sudo patch > coherence_patch.txt" do anything to the UpnpSource.pyc file?

Instead of running patch (because the ==== part was giving me syntax errors), I saved the modified UpnpSource.py file and copied it over to the /usr/lib/rhythmbox/plugins/upnp_coherence directory, but still not seeing any songs in my share (though a share does show up).

i tried xbmc as well
waited 15 min for anything to show up under upnp:// and nothing did. Not sure if there's a URL or port i need to fill in. 
You guys weren't kidding when talking about minimizing it - pretty program, but really not user friendly when running other apps.

---

### Post by peedeeramone on 2010-01-28
i had previously tried the simplify media daap file. it didnt really affect anything, so i cant completely verify that. i essentially just followed the instructions that loco gave (i believe with just a minor tweak) and it all worked quite nicely except for one machine, but i think its more on my copy of rhythmbox than anything else.

i tried looking into upnpsource.py but it has a later modification date than the coherence patch so i dont think, but i dont really know. by the ==== part i assume you mean the lines under index: in the coherence_patch.txt file. im not really sure how patches like this work but you could try removing them and seeing how that works out for ya. i also assume you ran it from the same directory.

in xbmc i just went to add upnp source and the simplify shares were all there. you just go into the music folders and thats where your music is.

good luck

btw if anyone else happens to read this and gets it working drop a quick comment. i would like to get a couple of more confirmations so i can mark this as solved

---

### Post by Pork Chop on 2010-01-28
not sure what i did the first time around, but originally, going the upnp route (before adding the patch), in rhythmbox I was able to see:

()Firefly svn-1696 on [simplifymedia server box account]
---() Home:username:Home

Clicking on the library only had 22 artists and maybe 30 tracks (should be hundreds of artists and tens of thousands of tracks).

Next, I copied that modified UpnpSource.py file over and now i just get the first line:
()Firefly svn-1696 on [simplifymedia server box account]

it also shows no tracks

When i run the daap share script bundled with simplifymedia, it kills my daap share plugin in rhythmbox, giving me a pop up window telling me that it can't be loaded.

I deleted all the files under ~/.gnome2/rhythmbox/plugins/daap/

As far as rolling back the UpnpSource.py; the revision number changes as part of the coherence patch:
--- /trunk/Coherence/misc/Rhythmbox-Plugin/upnp_coherence/UpnpSource.py (revision 949)
+++ /trunk/Coherence/misc/Rhythmbox-Plugin/upnp_coherence/UpnpSource.py (revision 1473)

I'm not sure what else would be different.

I think I may have tried running the rhythmbox daap plugin script before copying the patched py file over. So that may have been what broke the few songs I was getting before.

with xbmc, yeah i was never able to get the upnp info to show up.

While writing this post i went back into simplifymedia and noticed that the "enable upnp sharing over local network" checkbox hadn't been checked, so i just did that.
Amazingly, the Home:username:Home showed back up.
OH WOW! It finally started working!
Guess I skipped that step the first time around.

leave this up for other folks like me who missed it.

---

### Post by Loco Ulysses on 2010-01-28
I really don't know why patch wouldn't work, but I've attached my patched UpnpSource.py if anyone wants to try that.

The .pyc file is (I believe) compiled when you repeatedly use a .py file, and python surely checks to see if the corresponding .py file is new/changed before running off the compiled version, so it shouldn't be a problem. Deleting (or renaming) it should be safe though if it is a problem.

Also, *to run XBMC in windowed mode* start it and then hit the backslash key, "\". There should really be a menu or command line option or something, or it should at least be better documented. I only found that at the bottom of [this page]("http://xbmc.org/wiki/?title=Global_Keyboard"). You can minimize in windowed mode as well, although I prefer using Alltray to put it in my tray, and setting Compiz window rules so it's on every desktop and skips the taskbar.

---

### Post by peedeeramone on 2010-01-29
yeah i forgot to mention that you have to enable the plugin in rhythmbox.


how are you using firefly and simplify or am i just misreading that?

---

### Post by Pork Chop on 2010-02-18
> **peedeeramone said:**
> yeah i forgot to mention that you have to enable the plugin in rhythmbox.


how are you using firefly and simplify or am i just misreading that?

sorry for the late reply 
simplify broke on me again
just copied over the patched UpnpSource.py file and so far so good.

I don't know how i'm using firefly, i just know that's what's showing up in my rhythmbox window

---

