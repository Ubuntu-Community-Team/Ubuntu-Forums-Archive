---
title: "amaroK &quot;forcing&quot; file association for mp3"
date: 2008-05-18
forum: Multimedia Software
---

### Post by agostonbejo on 2008-05-18
Hi!

I'm using Ubuntu Feisty. I have both amaroK and XMMS installed. I would like XMMS to be the default application for mp3 files. Therefore I have tried the following:

kcontrol -> file associations -> mp3 
move XMMS up to the first place
Apply
-> the system SEEMS TO apply the changes. Now if I call the default application for an mp3 file  (e.g. by clicking enter on on it in Krusader or left-clicking on it with the mouse in Konqueror), it's still amaroK that will start playing it! Moreover, if I start kcontrol again and go to the file association settings for mp3's, it's amaroK at the first place again!

This seems a tad too intrusive for me. Does anyone know how to make amaroK understand it's not supposed to be the default application for mp3 files?


Thanks,
Agoston

---

### Post by alexforcefive on 2008-05-18
You check the radio button to set file associations. I think the list of applications goes in alphabetical order, which would explain why it keeps being reset ;)

---

### Post by agostonbejo on 2008-05-18
Hi!

I'm not quite sure you and I are talking about the same thing.

Please have a look at the screenshot I have attached:

a) I can't see any radio buttons there,

but

b) on the right hand side you set up "Application Preference Order" - this pretty much suggests it's got nothing to do with "alphabetical order", doesn't it? (Why would you be able to move items up/down otherwise anyway?)

Also, I have used this feature about a hundred times in the past, and it always worked.

I have to correct myself as well, though: the preference also seems to be restored for any of the file types (I have tested it with 'pdf' as well). It's also interesting that if I run kcontrol as root, the setting _will_ remain permanent. (Only for root, though.)

So the question still stands, but in a more general way: if edited with an ordinary user, the 'application preference order' setting for file associations keeps getting lost - what can be the problem and how do I prevent that?

---

### Post by alexforcefive on 2008-05-18
That's because I was talking about gnome even though you were asking about kde! :D Sorry!

---

