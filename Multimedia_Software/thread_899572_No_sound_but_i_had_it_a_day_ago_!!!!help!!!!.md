---
title: "No sound but i had it a day ago !!!!help!!!!"
date: 2008-08-24
forum: Multimedia Software
---

### Post by OSUfrk09 on 2008-08-24
OK My there is no sound on my computer. I have installed Ubuntu through windows. v8.04. I have a desktop  Compaq Presario. What i don't understand is that sound has worked on my computer for the past few days but stopped working. I don't know if any of the updates did something or what. I have a Creative sound card but that doesn't function or i don't know how to make it function with ubuntu so i use what the computer already had. but i noticed when i login and the sound i plugged into the creative sound card i get the login sounds but music or any other sound does not work. I have tried multiple things. The sound is NOT muted and volumes are not down. I have also tested my speakers on windows and they work. Please Help...

---

### Post by markbuntu on 2008-08-24
It is difficult to understand what you are saying but if you get the login sounds you can try this. Make a new user in System/Adminstration/Users and Groups. Then logout and login with the new user and see if your applications play sounds.

---

### Post by ajgreeny on 2008-08-24
What sounds are you trying to play, as it may simply be that you need codecs for the file types you are trying to use.  Do any sounds apart from the login sound play?  Try finding an ogg file and see if that will play.  If it does, it points to codecs being needed as I said.

---

### Post by OSUfrk09 on 2008-08-24
I created a new user and it doesn't work as well. I tried the .oog file and it didn't work. Let me try to make this clearer. When i have my speakers plugged into the creative sound card... and i login i get the drum beat sound. When its plugged into the computers stock soundcard... i get nothing. When i go to play music files, youtube, any sound... i don't get anything with either sound card.

---

### Post by edvar on 2008-08-25
I had the same problem... Take a look here: 

[http://ubuntuforums.org/showthread.php?t=894982&highlight=sound+login](http://ubuntuforums.org/showthread.php?t=894982&highlight=sound+login)

I'm not quite sure on what fixed it but I detailed everything I tried there...

---

### Post by markbuntu on 2008-08-25
Ok, so you get the login sound through your soundblaster card but nothing else with either card. You can try my troubleshooting guide:


[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

If you read it you should be able to get an idea about getting both of your sound cards working. The key to that is using the Pulse Audio Volume Control (pavucontrol) and having all the plugins, etc and making all the oss and alsa apps go through pulse audio. There are also links to a lot of the other troubleshooting and info threads and wikis.

I have 2 sound cards and have no problems using them both. It took a while to figure it out......

---

### Post by OSUfrk09 on 2008-08-25
ok so after countless hours of trying to solve this problem.... I will try to help those who have a similar problem to me... I tried everything. from unloading and reloading divers to checking to see if the sound was muted on the volume bar. Well after all this... it was a simple fix. Open your terminal and type in *alsamixer*  then procede to see if the master and/or PCM sound meter is turned down or muted... if muted then a [COLOR="Silver"]grey[/COLOR] [COLOR="Black"][/COLOR]mm will appear under the bar. to unmute press "m" on your keyboard and it should change to double 00's in [COLOR="Lime"]green[/COLOR] [COLOR="Black"]use the arrow keys to change the volume. I hope this helps your issues and you don't have to work as hard as i did to end up it being a simple thing like that. :)[/COLOR]

---

