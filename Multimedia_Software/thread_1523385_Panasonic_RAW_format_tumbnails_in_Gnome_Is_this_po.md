---
title: "Panasonic RAW format tumbnails in Gnome? Is this possible?"
date: 2010-07-03
forum: Multimedia Software
---

### Post by cogvos on 2010-07-03
Dear all,

No idea if this is the correct forum to post this.

I have a Panasonic G1 digital camera this outputs raw files in Panasonic's own format (suffix .rw2). UfRaw and RawTherapee can both read these so I can work on them in ubuntu (though ufraw displays a very overexposed image at first). f-spot has problems and displays a funny pinkish mess.

Can I get F-spot to display .rw2 thumbnails?

I would actually like to get Gnome to be able to display panasonic raw thumbnails as well. Is this possible?

As an aside it would be one in the eye for windoz as Panasonic have not released a codec for XP, only for Vista and 7 (and it seams to have a nasty hook in it according to dp review)

Cheers

J.

---

### Post by cogvos on 2010-07-03
Hmmm...

Been playing around and found this thread...

[http://ubuntuforums.org/showthread.php?t=1501632](http://ubuntuforums.org/showthread.php?t=1501632)

Which suggested installing libopenrawgnome1. I tried this on at 9.10 install but without success. There is a suggestion that I need to delete failed thumbnails, but I don't really understand.

Can anyone help?

---

### Post by cogvos on 2010-07-04
Hmm more playing around - still no success :(

There is an article - here [http://www.penguin.cz/~utx/gnome-dcraw](http://www.penguin.cz/~utx/gnome-dcraw)

Which is very complex and somehow makes gnome display raw thumbnails. Except I cannot get it to work. This does not mean that it's wrong, its just that I could not find all the files it refers to - it talks about /usr/share/application-registry/gimp.applications which does not exit for me and I had to add rw2 to some of the mime files as this is the file type for Panasonic raws.

Can someone have a look at the article and see id they can get it to work. so far I have gone from the funny binary icons to just black squares but still cannot get the thumb nails to work.

Help?!

---

### Post by cogvos on 2010-07-05
Well yeeeehar! (ahem)

Re thumbnails - To answer my own question yes it is - but an absolute pain.

- Important -

I am very new at all this. As a result I may be completely wrong and you follow these instructions at your own risk. I am not responsible for any damage that might be caused to your PC, data or anything else by you trying this out. In short it worked for me it may not work for you. (and in my very basic Linux knowledge is far too complex.)

Read the article here

[http://www.penguin.cz/~utx/gnome-dcraw](http://www.penguin.cz/~utx/gnome-dcraw) 

very carefully - I did not write this so please refer any questions to the original author.

It gives the bare bones, but I had to change the files dcraw.xml and dcraw.mime  to include .RW2 and .rw2. I'm guessing that they are alphabetical for a reason so I placed .RW2 and .rw2 in them alphabetically.

You need the latest (or at least version 8.88 which is the 1st to include Panasonic raw support) version of dcraw. Note the one in the basic install of Ubuntu 9.10 will not work.

I've  used the version of dcraw-thumbnailer that generates the thumbnails out of dcraw as I haven't a clue if Panasonic Raw files have embedded thumb nails. It is slow but works.

*Don't forget* to make dcraw-thumbnailer executable! I did and spent a day wondering where I had gone wrong.

There is stuff in [http://www.penguin.cz/~utx/gnome-dcraw](http://www.penguin.cz/~utx/gnome-dcraw) which is supposed to make gimp the default application for opening raw files. I cannot get this to work as I cannot find the file /usr/share/application-registry/gimp.applications. You may have better luck.
 
Note if you follow all this and end up with black squares rather than thumbnails in nautilus you have gone wrong somewhere, but please don't ask me where, and will need to clear out the failed thumbnails by using 

rm ~/.thumbnails/fail/gnome-thumbnail-factory/*

I think this needs to be at the top level of wherever you have you raw imaged stored. For me this is 

/Pictures/Raws

as that is where my raw images are stored yours may be differen and I have no idea what ~/ means at the start of the path

Good luck!

I have not managed to get f-spot to open raw images at all, or the gimp for that matter ufraw just crashes when I try :(

---

