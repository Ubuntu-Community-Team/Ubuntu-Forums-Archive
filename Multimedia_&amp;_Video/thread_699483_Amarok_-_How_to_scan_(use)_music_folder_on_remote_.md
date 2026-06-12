---
title: "Amarok - How to scan (use) music folder on remote PC machine"
date: 2008-02-17
forum: Multimedia &amp; Video
---

### Post by PiggiePaul on 2008-02-17
I've done some searching and there seems to be some "Similar" issues, but not quite what I'm finding, so I'm trying a fresh question.

I've downloaded Amarok (due to recommendations on here) and it looks very good. Well impressed.

However there is just one problem I'm having.

I have a Windows PC (acting as a kind of server) and I keep my music in a folder on the machine.

When I click the small (blue gears) icon called "configure folders" all I can see are locations on my Ubuntu system for it to scan for music.

How do I get it to scan and use a folder which is on a PC in a shared folder on my home network?

Thanks.

---

### Post by caseyg on 2008-02-17
Try using SAMBA. It works well for file sharing across operating systems.

---

### Post by PiggiePaul on 2008-02-17
> **caseyg said:**
> Try using SAMBA. It works well for file sharing across operating systems.

Thanks for the reply.

After some reading I just downloaded [COLOR="Blue"]Smb4K[/COLOR] which (if I understand correctly) is a Gui Samba front end.

Although how it's going to help me yet is still a bit of a mystery?

---

### Post by PiggiePaul on 2008-02-17
Just to update.

As  I said, I downloaded smb4K (supposed to be a good gui front end Samba program) if I understand that right?

Using this program, I simply browsed to my Windows PC.

It asked about passwords and do I want to store on a Keyring, but it warned about others accessing keyrings, so I said no.

And (as I say) I just browsed my remote folders, thinking, errrr, yes, and now what?

Then noticed (mysteriously) a new folder called smb4K had appeared in my home directory. And inside this was all the locations/folders from my remote PC.

As if by magic!!!!

Now, Amarok can just be pointed here and it works.

So, it works, only to be presented with a new Amarok issue.

I have a folder, with 1000 mp3 files (on the remote PC) and when Amarok opens it (you click on the little "+" sign in Amarok beside the folder name. Amarok goes grey and freezes for about 60 to 90 seconds before all the files appear.

---

### Post by PiggiePaul on 2008-02-17
Just an update.

When I open up the folder (in the left "collection" pane) of Amarok, the CPU loading goes up to 100% whist the Amarok window goes grey for about 1 minute, before it displays the 1000 files within.

I turned off the auto scanning/updating of folders but that made no difference.

Yes, I can understand it taking a few seconds to pull in 1000 filenames over the network link. 

If I just browse to it (via normal methods - not using Amarok) it takes about5 to 6 seconds for all the filenames and mp3 icons to appear.

So why it's taking amarok a good minute with 100% cpu loading I don't know :confused:

---

### Post by Sokertes on 2008-02-17
I have notice in the past that Amarok is a CPU hug. I used to use xmms but noticed that it has not been kept up for upgrades in a long time. I switched over to Audacious which is very much like a love child of XMMS and Amarok and it is much less CPU intensive than Amarok. It may not have ALL of the amenities that Amarok has but like I said..... it uses very little CPU


Just a thought

---

