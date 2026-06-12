---
title: "[SOLVED] Batch refresh ID3 tags?"
date: 2007-12-16
forum: Multimedia &amp; Video
---

### Post by Fjatle on 2007-12-16
Hi all!

First of, I am using Ubuntu Linux as operating system, and have
been using Sound Juicer as my cd ripper.
I am having some hard time with ripping my CD's.
When I found out that I could stream music from a media server
to my PS3, I started to rip all my CD's to my PC.

I am now about 50% finished, and I now realise a problem.
My PS3 do probably not recognize the ID3 tags on my ripped music.
I cannot find it under "music" category in my PS3 menu. However, I 
can find them, if I go through "PC Directory" in the PS3 menu, but
then I cannot shuffle all songs, and that all those features I get 
from the "music" category.

I have downloaded some somgs from the Internet. And those are the
only ones that is showned in the "music" category in my PS3 menu.

---------------

So, here comes the question:
Is there any software (for linux) that can batch through all of my mp3's
and refresh/clean up the ID3 tags? 

(I have tested now to rip with "grip cd ripper" and this one worked with 
my PS3. But i REALLY do not want to start from scratch again!!
So help will be very much appreciated)

---

### Post by ron999 on 2007-12-16
Hi
The one that I use is EasyTag.
With this you load it with a folder of a ripped CD and it looks up the info on a CDDB data base.
Then it lets you enter the fields and click through them to check if they're OK, or edit them, then save.
Maybe it will do the job for you.
EasyTag's in the Ubuntu repository, you can install it using Synaptic.
8)

---

### Post by rainwalker on 2007-12-16
I would recommend tagtool
It's in the repos, just search Synaptic for "tagtool" and it will be installed under Applications > Sound & Video > Audio Tag Tool

---

### Post by Fjatle on 2007-12-17
Easy tag is not that easy to me. Should call it Advanced Tag :)

Audio tag tool has a very easy interface, but I cannot find any option for getting the disc info
from the internet..

So I guess Easy Tag is the only one that can handle the job, but damn, the interface make no
sense to me :)

So..... so far I have now been typing in the CD info manually in Audio Tag too.
What a freaking long time job I am looking forward do \\:D/

---

### Post by ron999 on 2007-12-17
Hi, here's a how-to. So you can re-tag your mp3s one album at a time. (EasyTag for dummies :mrgreen:)

When you start EasyTag it will say 'searching', you must click on '**stop search**'.
Down the left-hand-side is a list of your computer's folders, click on the folder of the ripped album, and this time let it do the search.

A list of tracks will then appear down the middle of screen. Right-click the list and 'select all files', they will turn grey. Then right-click the list again and 'CDDB Search files'. It will go on the www to find the info.

Then it will give you suggested album(s). Click the correct one and a list will appear next to it on the right. Right-click on that list and 'select all files', then 'Apply' then 'Close'.

Then click through the track list and view the tags on the right one at a time. If they need correcting, do it now.
Then when you're finished click 'save'. (The floppydisk icon at the top).

This has got to be easier than typing each one manually - life's too short!
:cool::guitar::cool:

---

### Post by Fjatle on 2007-12-17
Thank you!

Well, Easy tag appeard to be even easier than that. 
You see, Audio Tag did not recognize the ID3 tags from soundjuicer.
That made me abel to check that Easy Tag actually tagged the mp3's correctly.

Easy Tag DID understand the tags from soundjuicer. That was actually one of the problem in 
the beginning, because Easy tag read the mp3, and saved it. The ID3 tag appeard to
be identical as it was before I saved. 
So I couldn't tell if Easy Tag actually made any changes to my mp3.

But then, I took som sample Mp3's and checked with Audio Tag that changes has been made.

And voialà, now I simply set Easy Tag to search trough ALL of my mp3 at once, and simply
made it re-save all of them. 


......So thanks alot for making me try Easy Tag just once more 	=D>

---

