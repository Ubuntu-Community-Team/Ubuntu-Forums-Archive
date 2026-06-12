---
title: "IR Webcams"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by gushy on 2006-06-14
Hey Guys,

Can anyone recommend an IR Webcam?  I'm looking to setup some webcams as part of a security system (using motion / gspy etc.) and ideally I need a camera that will have IR so that I can still capture at night.

I don't know if things like IR are purely software driven or whether switching to IR is something on the firmware on a camera.  I've spotted IR webcams like the [MSI Starcam 370i]("http://msicomputer.co.uk/Products.aspx?product_id=703634&cat_id=190") but of course they always say they only support Windows.

---

### Post by Keith_Beef on 2006-06-14
[QUOTE=gushy]Hey Guys,

Can anyone recommend an IR Webcam?  I'm looking to setup some webcams as part of a security system (using motion / gspy etc.) and ideally I need a camera that will have IR so that I can still capture at night.

I don't know if things like IR are purely software driven or whether switching to IR is something on the firmware on a camera.  I've spotted IR webcams like the [MSI Starcam 370i]("http://msicomputer.co.uk/Products.aspx?product_id=703634&cat_id=190") but of course they always say they only support Windows.[/QUOTE]

I think that the sensor inside just about every webcam is sensitive to light in the infra red range. But off the shelf, the webcam has a filter that blocks the IR.

Dismantle the webcam, take out the IR blocking filter and replace it with an IR pass filter.

Try this:
[http://www.hoagieshouse.com/IR/](http://www.hoagieshouse.com/IR/)

Beef.

---

### Post by gushy on 2006-06-15
hmmm, that's definitely an option as I have a webcam that's not working right 100% of the time so it is a perfect candidate for pulling apart; however I'm ideally after a camera that will record IR/B&W in the dark and colour when it's light, as opposed to a permanently IR camera.

---

### Post by keke21 on 2006-06-15
[QUOTE=gushy]hmmm, that's definitely an option as I have a webcam that's not working right 100% of the time so it is a perfect candidate for pulling apart; however I'm ideally after a camera that will record IR/B&W in the dark and colour when it's light, as opposed to a permanently IR camera.[/QUOTE] If you don't mind getting IR all the time along with the color, you can leave out the filters altogether. You'll just notice that friends might wonder why your lights are so bright.

---

### Post by gushy on 2006-06-15
Well this isn't to be used as a webcam, it's to be used as a security cam, so as long as the pictures are clear I suppose IR during the day would be acceptable.

---

### Post by Keith_Beef on 2006-06-15
[QUOTE=gushy]hmmm, that's definitely an option as I have a webcam that's not working right 100% of the time so it is a perfect candidate for pulling apart; however I'm ideally after a camera that will record IR/B&W in the dark and colour when it's light, as opposed to a permanently IR camera.[/QUOTE]

Hmm...

You might just end up with an IR camera that's not working 100% of the time. But it might be good enough to test the theory, then you could buy another one and do the same modification.

How about putting two of these cameras together, one "off the shelf", the other after the IR mod. Set them a little distance apart, like 6inches or so. Then use software to recombine the two images to give a sort of "relief enhanced view".

There was an article on Slashdot about a similar technique being used to take photographs for illustrating technical manuals such as automobile repair manuals. I wish I could find it again...


Beef.

---

### Post by gushy on 2006-06-15
that's something I'm considering, well two cameras I hadn't thought of combining the images.

I'm struggling to find detail on any webcams that says the IR lights are turned on via firmware linked to a light sensor, so an always on IR cam is probably the way I might have to go.

---

### Post by gushy on 2006-06-15
I've just spotted the [Genius Trek 310]("http://www.gadgetreview.com/2006/01/genius-videocam-trek-310-infrared.html"), seems like it would do the trick.  Don't suppose anyone has experience of this under linux?

---

### Post by hartz on 2007-05-04
I (unfortunately) have experience of the Genius Trek 310 camera NOT working under Linux.  It has got a Sonix chipset and it sends back its video in a very strange format.  At least the one that I have does - these things tend to change as fast as the manufacturer finds a cheaper source of components.

The pics are not particularly great either ... this is me playing with the camera.  Despite appearances I am not naked in these pics, I am wearing some shorts.  The pictures were all taken in near or total darkness.
[http://hartz.co.za/webcam-pics/](http://hartz.co.za/webcam-pics/)

I used Dorgem under Windows.

I am about to give the camera another try user easycam2 under Linux, I just want to compile 2.6.21 first....  I'll post back when I have some results.

---

### Post by gushy on 2007-05-04
oh that's a shame, I'll be interested to know how you get on with easycam2.

---

### Post by bobe84 on 2008-04-03
I patched gspca so now it works fine with Msi starcam 370i, problem is with brightlight because it bends color spectrum. Haven't yet (don't have time) made ir work but i will.
I you like i can send you gspca driver that works with msi starcam 370i.

---

### Post by FrankVdb on 2008-04-03
If you want to use IR for night vision you will need IR light. 

That means you will need to install an infrared light emitting lamp, which may cost you more than what you paid for your webcam. 

During the day, objects reflect the sun's infrared light in various degrees. If there is no light, there is no infrared light either.

---

### Post by bobe84 on 2008-04-03
Good point, ir led on msi starcam reach max 4m. You should think of external ir light source.

---

