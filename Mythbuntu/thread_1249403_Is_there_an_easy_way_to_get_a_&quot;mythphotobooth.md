---
title: "Is there an easy way to get a &quot;mythphotobooth&quot;?"
date: 2009-08-25
forum: Mythbuntu
---

### Post by geekyhawkes on 2009-08-25
I have pretty much got my myth setup finished now (apart from acpi which i will do later) and was thinking i would like to use a frontend as a photobooth for a party i am having.  

My thoughts are, setup a usb webcam and a front end with very simple press enter for picture interface.  The picture could then go onto my NAS and all the other front ends in the house could then play the slideshow using the myth interface.

I think this would be fun but my questions are;

will i need some kind of background script to run to update the database entries of the pictures so the slide show auto updates?

Is there some form of linux app (like cheese maybe) that will just take pictures every say 5 or 10mins and always save them to a specified location with no user input (im thinking for an extra camera mounted in my kitchen for example just to capture images).

Any input welcome, i think this could be kind of fun at a party, especially as the night rolls on (plus should raise myth a bit more as far the waf!)

---

### Post by geekyhawkes on 2009-08-29
Anyone have any idea how i could crack this?

---

### Post by nasha on 2009-08-29
I don't have much technical advice to offer, but you seem to have it pretty right. In my eyes all you would need is a program to take the pictures every so often, which saves them to your NAS. Then, as you said, you would need a script of sort that will update the DB, and then all frontends will be able to display the images. Provided mythtv is configured to grab pictures from your NAS location.

I do like the idea though... Certainly neat for parties where you could have a running slideshow of the night up on a screen somewhere. Best of luck getting it running! :)

Nasha

---

### Post by movieman on 2009-08-30
You might want to look at zoneminder: you may be able to configure it to record every few minutes and it's somewhat integrated into MythTV if you install the relevant plugin.

---

### Post by geekyhawkes on 2009-08-30
Thanks,  i will have a look at zoneminder.  I will report back if i get some sort of working solution.

---

### Post by geekyhawkes on 2010-01-23
SOrry to bring this up but i really didnt get anywhere making a script for this.  I am still after some sort of "mythphotobooth" plugin that would allow as described in the first post some sort of party mode that would update the myth photo player automatically in the background (say every 5 mins).

I am guessing it could be ran as some sort of cron job, or even as a temp script from a terminal, but I havent really got any idea how to implent it! 

All help/steers well recieved. 

Thanks

---

### Post by nickrout on 2010-01-23
Use a program called cheese. Its not a myth plugin, but will do what you want.

---

### Post by geekyhawkes on 2010-01-24
I have seen cheese before, but how to i get mythgallery to auto update in the background say every 5 mins or so?

---

### Post by nickrout on 2010-01-24
I don't think the database needs updating for photos.

---

### Post by geekyhawkes on 2010-01-24
Ok thanks, i will give it a try.  I had thought it might need updating as their is an import option with the gallery.

---

