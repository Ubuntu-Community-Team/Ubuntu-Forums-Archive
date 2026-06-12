---
title: "Where is photo workflow?"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by graphius on 2007-01-04
I so some semi-professional photography. In Windows I download my RAW photos onto my local hard drive. I then preview them with Fastview image viewer, or Adobe Bridge, deleting the "not quites"...
I then work on the "keepers" in Photoshop and save them onto my networked raided server. The "almosts" are also stored on my server.

I have been playing with k/ubuntu for the last few months, and I still can't find a decent workflow. Many programs like f-spot, kimbada, etc show a lot of promise, but they all seem to require me to store all my photos on my local drive. Not only is this not possible (I have A LOT of photos) I don't feel comfortable with all my photos on one HDD. Also they seem a bit kludgy when it comes to working with RAW (especially with my Fuji SLR).
I don't know the Gimp as well as I know Photoshop, but even so, I cannot get images quite the same out of it. I don't know if it is 8-bit vs. 16 bit, or colour workspaces, and to be quite frank, I don't care. It won't work for me.

This was not meant to become a rant. I love a lot of things about kubuntu, Linux, and OSS in general. In fact I would like to help out a promising project if I could (I am not a programmer, just an artist and a management type) but I find myself having to reboot to get back to windows more times than I would really like. It is a pain in the neck!!

I guess I am wondering if anyone else has found a serious set of photo tools? These would include:
[LIST]
[*]a browsing program, preferably with tagging and searching options. It should also recognize RAW files (dcraw is great)
[*]a decent RAW converter
[*]a good image manipulation program (maybe Gimp will come to the plate soon)
[*]Full network support (some of my linux newbieness may be to blame here)
[*]colour calibration compatible with hardware monitor measurement
[/LIST] 

As I said, I love a lot about kubuntu especially. Any suggestions?

---

### Post by encompass on 2007-01-04
Linux comes with great network support... problem it is so well, most people don't know where to start.
NETWORK:
If you want to share files on your network.
    If you use only linux... you may link to just use ssh, pretty easy.
    If you use anything else, try samba networking.
If you want to share files over the internet with others.
    Ssh is the securest way to share files with your other computers over the internet.
PHOTOEDITING:
Did you know the adobe photoshop can run in wine.  I hear many reports of it.  Email adobe and ask them to make adobe for linux.  Then install the wine way.  That way you have your adobe.  Gimp is great for me, and I think anyone using photoshop is overkilling things.  But that's me, I don't like photoshop because I don't use it.
As for your raw images... you could probably make a script that could do the converting.  But that is for yet another thread.

---

### Post by graphius on 2007-01-04
Thanks for your quick response. 

I have looked through all the forums. I have tried a lot of the solutions. None of them are quite ready for mainstream yet.
I do use photoshop. Not to be rude or anything, but maybe you don't know what photoshop can do. I have never used a gas stove until recently. Now I could never go back to electric elements. It is the same thing. I can make photoshop do some amazing things. Maybe I don't know the gimp well enough, but I find it doesn't have the control I need, and expect.
I have tried photoshop in wine. Again, it is a kludgy solution, slow and doesn't integrate at all with the OS.
the biggest hurdle though is a good browser/cataloging program.
As I said, I have tried a lot of them, but most require all the photos to be stored on the same hard drive. I would settle for a good browser that recognizes RAW. 
Right now I am using FastStone Viewer running on wine. again, a kludgy solution, especially when trying to edit a photo. In Windows, I right click and select Photoshop (set under options) In Kubuntu it will not recognize photoshop, or even Gimp.

I do appreciate these forums, that is why I am asking these questions. Like I said, I really like Kubuntu, and I prefer to use it for almost all my computer work. I am just stuck on this one issue. Unfortunately, I can do almost everything I normally do in Kubuntu on my windows desktop, and I don't have the graphics issue. I am almost tempted to run Kubuntu on a virtual server under windows. 
Now isn't that a backwards way to have to work:-k 
I hope I don't come off as a rant, or as unreasonable, I just keep starring at this smiley and relate too well ](*,) ](*,) ](*,)

---

### Post by graphius on 2007-01-04
PS, the networking per se is not an issue, I am using a samba share on my server (which happens to be running a linux flavour, SME server) so I can access things, I just can't easily browse (with thumbnails) my RAW files. 

PPS I am trying to set up symblinks, so that may solve the surface problems, however it is still a bit of a bandaid solution.

---

### Post by encompass on 2007-01-04
Wish I could help you more... but as it stands I don't see linux doing what you would like in that respect.  Sometimes windows has to be there... just not for me. :P
And I do understand the power of photoshop.  I see it all the time at school and I know it can do much more than gimp.  I just like gimp better.  I also, used too now, run a 700 mhz lappy with 200mb ram.  I ran everything in the console, even my videos, people thought I was crazy.  But crazy seemed to fit me.  I finally got a new computer.  People say the same things though.  Interesting....
Hope the best...
Jason

---

### Post by fx57 on 2007-01-04
MythVideo can do want you want. You can also edit the metadata to your heart's content. Basically make a video directory and set that as your video folder in MythVideo and then you can browse your files via MythVideo and launch it when you wish. You can edit the metadata and add thumbnails if you wish.

referers:[www.unreadedpost.com]("www.unreadedpost.com")

---

### Post by presspics on 2007-01-05
Hi Graphius! I feel your pain!

I'm a pro news photog who made the leap to Kubuntu just a month ago. 
(Okay, I shoot the Oly system but don't laugh. Great factory rep program.)
In Win, my most-used RAW app was Capture One with high-level post-processing done in PhotoShop. I also came to adore the plug-ins from power-retouche and DFT for 'sweetening'.

Yep. I tried Linux-Bibble for just one assignment and recognized it has major memory problems so out the door it went. I installed the beta of Crossover Office ([www.codeweavers.org](www.codeweavers.org)) and am able to run C1 Pro 3.7.5, but only in trial mode and with no colour profiles. I don't know what will happen when my 30-day limit is up...

However, I found RawStudio ([www.rawstudio.org](www.rawstudio.org)) and it is the FASTEST I've ever seen for rapid processing of RAW files in Linux. It uses dcraw and there are nightly builds available. It doesn't have the bells and whistles of C1, but it is super sweet. It also lets you colour balance JPEGs by temperature, which is nice. You've got to try it out! After you get your conversion, then stuff like NR and Un-Sharp can be done with your choice of tools (GIMP, Cinepaint, Krita [Latest release is v-e-r-y nice], or one of the older PShops that DOES run under Crossover or Wine.

For lightroom/aperture flavour, Bluemarine is in very early Linux development - but shows a lot of promise for pro use. I honestly didn't like the 'feel' of Lightzone. I found I spent waaay too much time on each image just to get it to the point where it was useable.

Basically, I'm finding instead of that one killer prog-for-all-needs, I've been picking single-use tools that are outstanding for what they cover. For batching? I do native res batch processing with Irfanview. (I did a Windows install, then copied the dir over to Kubuntu. It runs!!!! Now to see which PShop plugins can also make the leap...)

For NR and high iso stuff I use a windows NR prog from mediachance called PureImage. It smokes noise ninja. and for biggie-sizing there's another windows prog, BenVista photozoom, that installs and runs with Crossover. I used this prog extensively in windows and I like it being around. Oh! And Gimp 2.3.xx includes a Lanczos choice now for interpolation. 

Hope this helps!

---

### Post by graphius on 2007-01-06
Thanks Presspics, that is kind of what I was looking for. It also confirms my suspicions, I just need to dual boot for a little while still..:-? 
BlueMarine looks great, except it doesn't handle Fuji Raw yet. I will keep it on the radar though. Rawstudio seems to have problems too. Maybe I will just have to be patient (not my strong suit ;) ) 
As I said, I really like Kubuntu, and I use it for all of my non graphic work.
Thanks again.

---

