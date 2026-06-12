---
title: "Firefox can't find VLC"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by commodore on 2007-06-24
I have VLC's Mozilla plug-in installed but Firefox still says I'm missing a plug-in. I used to have Totem's Mozilla plug-in but Totem sucks so bad I threw the whole pile of crap out.

---

### Post by commodore on 2007-06-25
Do I have to edit a configuration file or something?

---

### Post by commodore on 2007-06-26
Please help me I can't watch anything online.

---

### Post by NilsE on 2007-06-26
Check out this thread (sticky in this forum) 

[http://ubuntuforums.org/showthread.php?t=413626](http://ubuntuforums.org/showthread.php?t=413626)

Also, you can go into edit/preferences/content/manage and pick the player for the file type. I installed everything and just pick the one that works best for the file type by experimenting.

EDIT: Your profile says Breezy so the link may not be perfect for you but still has good content.

---

### Post by commodore on 2007-06-26
My profile is wrong. I'm using Feisty. Thanks for the link. I only see three file types in that Download Actions list. What's wrong?

---

### Post by NilsE on 2007-06-27
> **commodore said:**
> My profile is wrong. I'm using Feisty. Thanks for the link. I only see three file types in that Download Actions list. What's wrong?
Check to see if you are on the latest version of Firefox in  Synaptic since it fixes that problem with download actions.

In the meantime go into about:config (in the locations box) and search for the workd hide.  A couple of options come up but the one you want to change is the one about mimetypes.  Change it from true to false by double clicking it.

---

### Post by commodore on 2007-06-28
I don't understand what to search for. Workd hide? Workd didn't have any results, I did something to an option that came up with hide and I do have more file types in Download Actions now. 

Does VLC even play xvid?

---

### Post by NilsE on 2007-06-28
Sorry, typo.  Meant to say search for the WORD "hide" and the setting you are looking for is the one that is about hiding plugins_without_extensions.  But it does sound like you found it if more is showing up in the download selection.

I am not sure if VLC will play xvid since even though I have it installed I don't have it playing anything in my selections. The key is to select players for the mimetype until you find one that works for you with what you have installed. I am probably one of the rare few who use and like Totem and all it's plugins since it works for me for most files.

Did you confirm what version of Firefox installed? Version 2.0.0.4 is what you want to be at.

By the way, [http://www.linspire.com/file_types/filetypes.php](http://www.linspire.com/file_types/filetypes.php) is a good place to test mimetypes with different players.

---

### Post by commodore on 2007-06-28
I made a mistake. I need divx not xvid. I tried that linspire site and both xvid and divx worked but when I go to [http://stage6.divx.com/](http://stage6.divx.com/) I can't see anything even with mplayer.

---

### Post by Peverel on 2007-06-28
Same problem here...
Doesn't work with Stage6 either... The Totem player plugin comes up but the screen stays black...

Any suggestions? Or how could I point Firefox to use VLC when accessing divx files?
I don't have that .divx ending in my manage contents list...

Thanks

---

### Post by Peverel on 2007-06-28
Hm, I just found this on the search, maybe it helps...

I'll check it out...

[http://ubuntuforums.org/showthread.php?t=432873&highlight=divx](http://ubuntuforums.org/showthread.php?t=432873&highlight=divx)

---

### Post by NilsE on 2007-06-28
I believe both xvid and divx are .avi so try changing that extension.

Also, if you click on the little option thing in the upper right corner of the manage window you can select mimetypes to show which gives you another column with more info on the file types.

---

