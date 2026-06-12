---
title: "Free DVD program with menu options?"
date: 2010-03-11
forum: Multimedia Software
---

### Post by Edward B. on 2010-03-11
*Someone in Beginners forum suggested I post there here... I'm sure this question has been asked before, so apologies if it's an annoyance. I would appreciate a link to any threads where this was answered.*

Does anyone know of any free DVD burning programs that will allow you to easily create a menu? For a wedding reception video, for instance, so instead of having to put the DVD in and watch the entire thing/fast forward, you could have a menu that would allow you to select, say, Ceremony, Speeches, Dance, Closing?

Thanks in advance for any help!

---

### Post by J_Stanton on 2010-03-11
devede can create menus. it is in synaptic or ubuntu software center.

---

### Post by alegallo on 2010-03-11
DVDstyler is my choice.

BUT remember that there is no program (that I know, at least) that makes all of the job.
I mean, both devede and dvdstyler will make a dvd structure for you, with menus and everything you need, but they'll produce a .iso image to be burned with any other burning program.

---

### Post by Edward B. on 2010-03-11
Okay, I am very ignorant about this stuff.

I need to burn an AVI file with menus.

Is what you're saying that I need to use one program to create a menu and another program to actually burn it?

What do you mean when you mention ISO? Can the programs mentioned only burn ISO files and not AVI? I know nothing about ISO files except that I made an Ubuntu install CD using one.

Thanks again for the help.

---

### Post by 2hot6ft2 on 2010-03-11
> **Edward B. said:**
> 
I need to burn an AVI file with menus.
A dvd contains VOB files which are mpegs not avi and I've done a lot but have never seen a avi file with menus.
> **Edward B. said:**
> Is what you're saying that I need to use one program to create a menu and another program to actually burn it?
yes
> **Edward B. said:**
> What do you mean when you mention ISO? Can the programs mentioned only burn ISO files and not AVI? I know nothing about ISO files except that I made an Ubuntu install CD using one.
An ISO file is an image of a cd or dvd, I guess you can think of it as a picture of the disc and burning it is printing it on the disc.

You create an ISO file which you can then burn to a dvd like you did with the ubuntu ISO. You can burn avi files to cd's or dvd's but it wont have menus unless you have a divx capable dvd player and even then the menu is rather crude at least it is on mine.

You were asking about creating dvd's which are not avi files so you have to understand that dvd's with movies on them do not use avi files.

If you want to make dvd's with menus then you're looking at converting the avi's to mpegs, creating chapters for the menus, and finally burning it to a dvd.

It's more involved than you're thinking so my suggestion is that you try one of the other suggestions like this one:
> **alegallo said:**
> DVDstyler is my choice.

BUT remember that there is no program (that I know, at least) that makes all of the job.
I mean, both devede and dvdstyler will make a dvd structure for you, with menus and everything you need, but they'll produce a .iso image to be burned with any other burning program.

The only program that did the converting and burning that I've used was Nero and that was in windows and there is a linux version but it's not free. I'm also not sure if it has all the same capabilities.

---

### Post by Edward B. on 2010-03-11
Thanks, 2hot. You're right, I really didn't understand that much and your explanation has helped me out at a lot.

I have a digital camera that records video, but only in AVI format - there may be a way to set it to record MPG instead, not sure.

Can you tell me if there is a free program available that will convert AVI to MPG?

Also - DVDstyler, for instance. Using this I could create a menu and then an ISO. I would then burn that ISO onto a disc. That would burn the content and the menu on the disc? Is that correct?

---

### Post by 2hot6ft2 on 2010-03-11
> **Edward B. said:**
> Thanks, 2hot. You're right, I really didn't understand that much and your explanation has helped me out at a lot.
You're welcome. It was rather obvious that you didn't understand the difference.
> **Edward B. said:**
> Can you tell me if there is a free program available that will convert AVI to MPG?

Also - DVDstyler, for instance. Using this I could create a menu and then an ISO. I would then burn that ISO onto a disc. That would burn the content and the menu on the disc? Is that correct?
Yes. That's what they do, AVI to VOB actually which is like MPEG2 I believe. You can actually take VOB files from a DVD and change the extension from .VOB to .mpg and play them in most players.

I would try DVDstyler like was suggested. You can also try QDVDAuthor or DeVeDe. I wasn't real impressed with DeVeDe but QDVDAuthor looks pretty slick.

They are all in synaptic.

Re-encoding takes a while so I suggest setting everything up then when you're ready to call it a night start it and it may be finished in the morning depending on how much you're having it do.

QDVDAuthor screenshot

---

### Post by Edward B. on 2010-03-11
Okay - quick question. I have DVDstyler and have created a menu with AVI files. 

Is there a way to transfer this to a DVD?

Right now I saved the filed as a XML file. Is there a way to save this as an ISO and then burn it?

Or do I need to convert the AVI files to MPG somehow?

EDIT: Just saw your reply - so I need to recode the file? How do I do this?

Thanks again for the help! I know it's frustrating when someone who knows nothing about this stuff pops in and starts asking all these questions, but I really do appreciate you taking the time.

---

### Post by 2hot6ft2 on 2010-03-11
When you started it and selected the language then it gave you a screen which included a place to drag and drop your files.

Then you need to go into DVD > Options and make the settings for your project.
And in Configuration > Settings
Select your background and buttons once you have all of it setup select Save so next time you wont have so many settings to mess with.
Then it looks like you click on the Burn Icon.

I haven't used it but it looks pretty simple and I'm sure it will ask for a disc unless it's going to make an ISO in your home folder.

Someone that has used that program should help with it.

It should recode the files automatically for you.
> **Edward B. said:**
> 
Thanks again for the help! I know it's frustrating when someone who knows nothing about this stuff pops in and starts asking all these questions, but I really do appreciate you taking the time.
It doesn't bother me if it did I wouldn't be here trying to help people.

---

### Post by 2hot6ft2 on 2010-03-11
If you're in the U.S. you'll want to set it to NTSC, PAL is for other Countries and may not work right in U.S. dvd players. That's about the only change I saw I would make.

---

### Post by Edward B. on 2010-03-11
Crap. Already started burning. Hopefully I selected NTSC.... although I think I just went with whatever was preselected...

I'm creating an ISO right now. Do you know if that is the way to go or should I just have burned it straight to the DVD or does it matter?

---

### Post by Edward B. on 2010-03-11
Okay, I keep trying to burn this thing with GnomeBaker and get this message:

:-[ WRITE@LBA=0h failed with SK=0h/ASC=00h/ACQ=02h]: Input/output error
:-( write failed: Input/output error

Is something screwed up with my DVD writer?

EDIT: When I use Brasero, it says that I don't have the plugins to support the DVD I have.... does this make any sense?

---

### Post by andrea000 on 2010-03-11
Try [2mandvd]("http://www.kde-apps.org/content/show.php/2ManDVD?content=99450") there should be a deb file for download or a
ppa for version 1.3.1 i just have not had time to look
for it yet.But you can build it from source.

---

### Post by cotcot on 2010-03-12
Edward, I would suggest to take some time to read carefully a manual like for example the [[COLOR="Red"]manual of dvd-styler[/COLOR]]("http://dvdstyler.sourceforge.net/docs/DVDStylerManual.pdf") or a [[COLOR="red"]qdvdauthor user guide[/COLOR]]("http://w3.linux-magazine.com/issue/53/Q-DVD-Author.pdf") or a [[URL="http://w3.linux-magazine.com/issue/53/Q-DVD-Author.pdf"][COLOR="red"]devede manual[/COLOR]]("http://w3.linux-magazine.com/issue/53/Q-DVD-Author.pdf")[/URL]. 
OK some of the examples are for older versions of the apps mentioned but besides a couple of different buttons or so they explain well the typical workflow for making a DVD. This will help you understand better the previous posts.

---

### Post by Edward B. on 2010-03-15
Thank you. I will look through the manuals. This is a lot more difficult than I envisioned! Something might be wrong with my DVD writer, though, as I also tried burning a single AVI file onto a DVD with no success. I read in another post that someone had trouble with the same brand that I am using - Memorex. I do not know if this could be a problem or not.

---

