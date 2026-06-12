---
title: "libreoffice writer icon will not minimize to unity panel"
date: 2011-02-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by jim11 on 2011-02-02
For every application other than libreoffice, the libreoffice writer logo on the unity panel will not retract back with the rest of the unity panel, and you cannot open the unity panel onto of another running application as you could before yesterdays update. Which I had to downgrade the libglue and libgluemx packages (from 1.5-1.5.7 to 1.5.-1.5.2) in order to get unity to run.

Screen shot is <s>attatched</s> below(Cannot upload attatchments from Unity interface).

[[IMG]http://img710.imageshack.us/img710/2811/screenshotsh.th.png[/IMG]](http://img710.imageshack.us/i/screenshotsh.png/)

---

### Post by coffeecat on 2011-02-02
I was getting this but with the Tomboy icon. And only with a maximised window pushing the dock to one side, not an unmaximised one as in your screenshot. Perhaps it depends where in the dock the icon is. LO for you; Tomboy for me. But now I'm not getting this. I can't remember when it went away but I installed some compiz updates an hour or so ago - perhaps they fixed it.

You say you can't upload attachments from Unity? I can - see my screenshot. What happens when you try? By the way, Imageshack is as slow as a glacier. It's very off-putting.

---

### Post by cariboo on 2011-02-02
> Screen shot is <s>attatched</s> below(Cannot upload attatchments from Unity interface).

That shouldn't have anything to do with Natty, as it is a forum function how are you trying to upload an attachment. I use manage attachments, like in the screen shot.

---

### Post by mc4man on 2011-02-02
> logo on the unity panel will not retract back with the rest of the unity panel
I see that happen from time to time, no app in particular, either a restart or a reload of compiz should resolve

> you cannot open the unity panel onto of another running application as you could before yesterdays update
You can, but random odd behavior is very likely. 
Right now I'd say unity/compiz is quite fragile, it may work just fine or break down in any number of ways depending on your activities 

Dependent on what's gone wrong you may need to do - move a window, usually to right,  a logout/in, switch workspaces, a restart, reload compiz or unity among other things.

You may find it useful to create a desktop launcher w/ the command of this, it things don't seem right then use it.
compiz --replace

If so the best place to put it is in the bottom right corner area of your desktop, that area is somewhat safe from various potential current issues

---

