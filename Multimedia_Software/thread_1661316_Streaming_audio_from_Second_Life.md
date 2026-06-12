---
title: "Streaming audio from Second Life"
date: 2011-01-06
forum: Multimedia Software
---

### Post by scottholmes on 2011-01-06
I haven't gotten an answer from Second Life fora so I thought I'd ask here.  I'm using Ubuntu (lucid) x86_64.  Totem, Rhythmbox etc all work correctly but I fail to get any streaming audio from any of the Second Life clients I've tried.  In some cases I can copy the media url into rhythmbox and run the sound from there but in most cases the url is "hidden".  

So, if there are any users of Second Life here that can help out I would appreciate hearing from you.

Scott

---

### Post by ChrisWebb on 2011-03-27
Here's what I did to get streaming audio working in SecondLife (Ubuntu 10.04 x64):

Assuming you've installed the SL viewer from Linden Labs...

edit the secondlife file in /opt/secondlife-install
```
gksudo gedit /opt/secondlife-install/secondlife
```UNCOMMENT the following entries at the top:
```
export LL_BAD_OPENAL_DRIVER=x

```and
```
## - Avoids using the FMOD ESD audio driver.
export LL_BAD_FMOD_ESD=x
## - Avoids using the FMOD OSS audio driver.
export LL_BAD_FMOD_OSS=x

```Notice that the # is missing from these lines.

Save the file and start Second Life again - you should have streaming audio :)

If not, check the audio preferences are set to default (Me-Preferences-Sound & Media-Input/Output devices)

---

### Post by scottholmes on 2011-03-28
That is what I did when I first experienced this problem, and it worked for a time too.  Actually, the problem has now become academic as Linden has chosen to display all urls.  I can now effectively copy the music url into rhythmbox from any sim.

---

### Post by ChrisWebb on 2011-03-29
Well it still works for me, but you do have to remember to re-apply the changes if you update the client since it overwrites the secondlife file.

---

