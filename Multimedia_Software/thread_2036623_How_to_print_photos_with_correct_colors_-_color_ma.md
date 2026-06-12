---
title: "How to print photos with correct colors - color management, darktable and gimp"
date: 2012-08-02
forum: Multimedia Software
---

### Post by gesti on 2012-08-02
Hello Everyone,
The following issue is the only one I have not managed to solve under linux since I switched my photo editing to linux.
I have read great many articles and how-to-s about this subject, but still I'm just ending up with so-so correct colours. (My latest try for example: the picture look gooded on pc, but when I print it a certain shade of green becomes slightly yellowish...)
After tons of wasted paper and ink I would like to get some advice how to do this properly.
Here is what I do normally:

[LIST]
[*]I adjust my RAW pictures in darktable
[LIST]
[*]first question raises here: *output color profile *- what do I set here?
At the moment *output profile* is set to *sRGB* and *softproof profile* is also set to *sRGB*; both *output intent* and *display intent* is set to *preceptual*. *Display profile* is set to system display profile.
I calibrate my monitor with a Spyder3 every now and then, so I believe the *display profile* from the aboves is at least set correctly. :)
[/LIST]
 
[*] export it to a file format that gimp can read (normally 8-bit JPEG as from some reason GIMP refused to open other formats for me.)
[*]in GIMP I don't normally edit pictures (as I like to show the truth :D ) so from here I just choose print. And again I'm just puzzled on the sheer number of options. There is *Print form Gutenprint...* and normal *Print...* ;
[LIST]
[*]the gutenprint doesn't work for me (I have the **gutenprint driver installed** for my printer) - it just said "*lp: Error - unable to queue from stdin - OK.*" then printer pulls the paper in then stops.
[*]In the normal print I just get some weird blacks and things that I wrote earlier. I have tried to adjust on the colours on the advance tab (options like: *Brightness, Magenta, Cyan, Yellow, Blacks*), but still couldn't get rid of all the faults in printing.
[/LIST]
 
[/LIST]
I know that I should get my printer calibrated too, but I'm just not sure if that is the only problem. As when I used to print in windows, the colours were ok; not great, but ok. Even without printer calibration.
So here I'm in desperate need of some advice on what am I doing wrong.

---

### Post by Rallg on 2012-08-02
That is a complicated question. As you expect, it is necessary to have a color management file (*.icc or *.icm) for your printer.

You didn't say what kind of printer it was, but I assume it is an inkjet type. Does the manufacturer provide a color management file? Inkjets are difficult for color management, unfortunately.

If you are printing to "real photos" (for example, a machine at a drugstore or photo store) then there is a good chance that the machine is made by Noritsu. Noritsu provides *.icc or *.icm files for its models, available online. If you don't know the model, search online for other experiences of the common models. I have done this, and it is clear that color management was very useful for such machine prints. Exception: Some machines may "correct" your colors, whether you like it or not.

You are looking at the monitor in RGB, but the printing is in CMYK. This conversion is does automatically for you, but it may be that on the Windows side, the driver software knows some adjustments that are not present on the Ubuntu side.

Via synaptic package manager, you can obtain a variety of generic and non-generic printer profiles (search for "icc" in the package name). Keep in mind that if your printer driver installed a color management file in Windows, then the necessary file may not be in Ubuntu. But the *.icc or *.icm file, if it exists, can be read by any system. So if you have one, you can put it into Ubuntu where the other color management profiles are located, and use it.

For the monitor, sRGB is probably OK. For my model laptop, someone took the trouble to calibrate the monitor, and the result was not very different from sRGB. You should know that the default screen brightness on Windows may be different that the default screen brightness in Ubuntu. If you find that the colors are generally more intense when processed one way or the other, then that may be the problem, solved by adjusting your default brightness.

The best way to soft proof is to have your image converted to the printer color space, and look for "out of gamut" areas. These are colors that appear OK on your monitor, but cannot be reproduced in print. Typically they are dark, saturated reds, greens, and blues (which require a lot of ink).

Some users suggest that gutenprint does not work with color management. I do not know for sure (the info may be obsolete).

Again, you asked a complicated question. I have compared color management results in Gimp (2.6) on both Windows and Ubuntu, same computer, and found results appear exactly the same when printed via Noritsu photo machine. But I don't know about inkjet results.

---

### Post by efflandt on 2012-08-02
What printer, and are there any adjustable settings on the printer itself?

When I originally got a Lexmark C543dn color laser, I thought that its default colors were too bold, which may be fine for attention getting brochures, but not photos.  So I downloaded a reference image that was a combination of various images and used up some toner adjusting the printer itself until everything in the print looked photo realistic to me.  So it works perfectly in Windows or Linux.

When I got the same printer for the office to replace an obsolete inkjet printer, I set the new C543dn to the same settings I worked out at home, and it was picture perfect just using settings on the printer itself.

So I would get an unaltered combo reference image and adjust whatever you need to for that to print perfectly. Then adjust your monitor settings to have it look the same on your monitor.

The only thing I normally do with gimp, other than scaling, is **Colors** > **Curves**, not to change colors, but to brighten up dark areas or smooth out high contrast.  I am not a pro, but have been taking pictures for probably 50 years.

---

### Post by coldraven on 2012-08-02
I just had some prints made at a Photo Lab and as Rallg says the results look like they have been corrected. The inkjet versions that I did at home look better.

I can't help you with the colours but I do have a good tip. Search for CISS and the model of your printer. CISS stands for "Continuous Ink Supply System".
I have an Epson Stylus Photo R300 with six colours. I had a CISS with external tanks, it worked three years before it failed. Now I have the refillable cartridges and they are behaving well. Ink costs £12 for 600ml. By comparison, ink for a Canon would cost £1000 a litre if you use their cartridges!

If Gimp will not load anything but jpgs then try reinstalling it.

---

### Post by Rallg on 2012-08-02
I re-read the original post. Ah, I see a potential problem:

Darktable works in high bit depth. That is, the color information is processed with more than 8 bits per channel. The file you save (depending on what you do) might retain the high bit depth, or be reduced to the 8-bit per channel depth that Gimp (prior to development version 2.9) understands.

Whether a program can open a high bit-depth file depends on circumstances. Some can open it and retain the bit depth. Some cannot open it at all. Others can open it, but will reduce it to 8-bit per channel depth. JPEG is (to my knowledge) never in high bit depth; but TIFF and PNG may be high bit depth.

If Gimp cannot open your files from darkroom, then ensure that you are not saving in high bit depth from darkroom. If you already have files like that, they can be re-processed down to 8-bit depth, so you haven't lost them.

Gimp 2.9 (development version) can be compiled from source code. I have it. However, Ubuntu 12.04 does not include sufficently many up-to-date libraries. To compile Gimp 2.9, you would need to bring in so many "backport" (not part of the distro) files that you would be better starting with Ubuntu 12.10 (development version). I do not recommend compiling Gimp 2.9 at this point in time, unless you are strong, since there are issues.

I don't use darkroom much, so I wasn't able to figure out how to set the color management. In Gimp (any version), I suggest the following, in Edit > Preferences > Color Management:

RGB Profile: sRBG
CMYK Profile: In most cases, *.icc or *.icm specific to your printer AND paper, or best match.
Monitor Profile: calibrated for your monitor, if available; otherwise sRGB
Display rendering intent: perceptual
Print simulation (softproof) profile: In most cases, same as CMYK profile.
Softproof rendering intent: perceptual
Mark out of gamut colors: yes, and use something conspicuous (such as a bright magenta, rarely found in nature) rather than neutral gray.

I warn you that Gimp 2.8 (and dev 2.9) has a reputation for being sloooow when using color management of any kind, at the time I write this.

If you do not have an *.icc or *.icm profile for your printer, then search the internet for advice from others. Be aware that the paper you use will make a difference. Presumably you are set up specifically for photo printing (rather then an ordinary office printer) so there should be info available. However, anyone using a standard printer on ordinary office paper should know that you just won't get photo quality no matter what you do, because your technology isn't designed for it.

There are some situations where your CMYK profile and printer softproof profile will be different. If you were in that situation, you'd be a professional who wouldn't be asking questions here.

Be sure that you are not double-correcting the color profile. I do not know, but am told that some printers have built-in color management that assumes the incoming photo file was NOT color managed. If your printer does that, then it's still worth your effort to look for out-of-gamut colors.

I am not a color photo professional. If you get into that, then you'd probably want to consider obtaining your prints from a calibrated photo printer. Such exist. For example, one local outfit charges about the same for uncalibrated photo prints (not inkjet) as does the nearby X-mart. But if you want calibrated prints that obey your color management, that costs more. A lot more. Professionals needs that. And, it really shouldn't matter whether your photo file (normally JPEG or TIFF) was prepared on any particular operating system with any particular software.

---

### Post by gesti on 2012-08-03
Thank you for all the answers. Now I have some things to try and test as soon as I receive my new set of cartages, as of course yesterday I run out of ink. :grin:
Yesterday just before I ran out of ink I managed to print 2 decent looking pictures by leaving all the printer settings on default and instead I set a "*Gamma*" filter in View -> Display Filters...
The only problem is I was unable to test the consistency with other pictures as of my ink shortage. :)

@efflandt: > What printer, and are there any adjustable settings on the printer itself?No, unfortunately (or fortunately :) ) there are no additional settings on the printer.

@coldraven: Thank you for the tip! Never heard of this CISS before, I'll definitely get a set once I feel comfortable with my prints.

@Rallg:
I have set those profiles that you wrote about (have to admit here, that I don't have the right color profile for the printer-paper duo as Canon only give profiles for canon paper... and naturally I can't get hold of canon paper, only from internet in BIG amount, so I use HP paper)
Now I just don't know where to switch to softproofing view? In the View -> Display Filters... Or in Edit -> Preferences... -> Color management: Mode of operation to print simulation?
When I set the "*Mode of operation*" to *Print simulation*, most of my picture is marked as out of gamma. (all the reds)

BTW: I use a Canon MX310 multifunctional printer/fax/scanner.

---

### Post by Rallg on 2012-08-03
In my version of GIMP (which you may not have, because I compiled a development version), the softproofing is in Edit > Preferences > color management.

No matter what you are using for color management, if a lot of your photo is "out of gamut" that is a BIG problem. Normally, only a tiny amount of your photo should be out of gamut (preferably none at all, but a little bit is OK).

Try this experiment: Take a nice photo, and make a copy so you can work only on the copy. Open the copy in Gimp. Enable color management the way that you think it should be set. In the photo, reduce color saturation and contrast so that it looks "washed out" with no bright or dark areas, and no areas of intense color. (Note that this would have to be done for every layer in a multi-layer image.) If the "washed out" image still shows a lot of out-of-gamut in softproof, then you have some kind of problem with the software setup. I do not know how to fix that.

But if the washed-out photo does not show out-of-gamut, it means that your original photo is too color-intense for your printer capability. In that case, you would either (a) make your prints at a "real photo" service, or (b) use Gimp to adjust your colors until they mostly fit in the gamut.

I'm not a photo pro, but I first came across this while preparing artwork for print (that is, mass-market print, not one print). The inexpensive printing technology limited the color gamut. But by using color management, I could see where my photos had areas that would not appear as expected in print. So, I manually adjusted color areas until the gamut was OK. The resulting colors were not "as originally intended" (because the printer could not do that) but the print result was the same "as I saw it on my computer" just before I sent it out or printing (because the printer could do that).

---

### Post by gesti on 2012-08-04
I've got GIMP 2.8. I actually use Archlinux, so I always have the most recent stable versions.

Tried the experiment you wrote. And when I desaturate the picture (specially the red colors) then the out of gamut areas disappear. So it's just the printer or the paper of which I use the color profile from.

The interesting thing is that, I use a color profile for Canon Pro Photo paper, but I actually use HP Semi-glossy photo paper. Now, when I printed a picture about a strawberry - which was really intense red -, on to the HP paper all the colors came out well. The same picture when I switch on the soft-proofing, for the canon paper, it shows the whole strawberry as *out of gamut*.
Is it possible that the paper could make such a huge difference?

> I'm not a photo pro, but I first came across this while preparing artwork for print (that is, _mass-market print_, not one print).That actually does sounds like you're a pro in colors :D

---

### Post by Rallg on 2012-08-04
Inkjet paper definitely DOES make a big difference. In fact, there are manufacturers that specialize in paper for image-quality color inkjet prints. These are places that do not have famous names such as HP, because they are not stocked in the X-mart stores. The paper is expensive!

Use your browser so search for "icc inkjet." Aside from the generic results, you will see that several specialty paper manufacturers provide *.icc or *.icm profiles for their own papers (for example, Harman).

Assuming that the printer's cartridges are full, that all equipment is in excellent condition, and that you are printing best quality, then what you get depends on several factors. Aside from quality of equipment, and quality of ink, paper is very important. That's because different papers are capable of holding onto different quantities of ink without smearing, as well as having diferent underlying brightness.

CMYK printing (including inkjets) uses four colors: Cyan, Magenta, Yellow, and black (Kohl). Think of each color on a scale of 0 to 100, where 100 means that a spot is holding the maximum amount of ink for that color (and the ink is of maximum quality). Then, perfect paper could hold up to 400 at each spot. But paper is not perfect. The actual amount of ink it can take is less than 400. The better the paper, the more it can take, which means that your color gamut is wider.

Although the CMYK colors are rather standard chemically and in terms of spectrum, in reality there are differences rom manufacturer to manufacturer, pertaining to things such as light-fastness, resistance to wear, and even "environmental correctness" (dyes made from coal tar derivatives versus vegetable products, for example).

When home users print pictures, they usually want bright, saturated colors, even if they are not true to nature. But commercial artists want exact colors for certain purposes (human skin and corporate logos). For example, there is a very specific shade of red that Coca-Cola uses in its product logos. The brightest red will NOT do, commercially. It must be THAT EXACT shade of red. Hence, color management. Thus, in a Coca-Cola ad, some other colors (such as sky blues) can be off-shade. But if the ad shows folks drinking the product, then the people have to look OK, too. Might have to sacrifice the green of grass.

If you'd like to experiment, find a place near where you live, which has a real-photo printer. That is, you can buy photos that look like they were taken from a film camera, after you input your digital files (almost always *.jpg). Where I live, many chain drugstores and X-mart stores have this capability. I can even send the digital file online, then go pick it up. The cost is surprisingly low. What you can do is make several copies of the same image, trying different color management strategies. Again, there's a good chance that the printer is a Noritsu model. (I'm told that Kodak models may re-adjust your colors.) Then, you do not need to worry about inks or paper. To avoid conusion, add a little text to each image, identifying what you did.

I would have guessed that Canon paper would provide a bigger gamut than HP paper, but apparently I'm wrong! Either that, or the out-of-gamut warning is being honest. Just because something is out-of-gamut does not mean that it cannot print. It only means that the printed color will be different from (less saturated than) what you might have expected based on the monitor. If you are using "perceptual" settings, what happens is that out-of-gamut colors are brought into gamut, but in-gamut colors are intentionally de-saturated so that the out-of-gamut colors, by comparison, look more saturated. Whether or not a strawberry looks bright red depends on what you compare it to!

Again, this is a complicated subject. I'm not a pro. Imagine what REAL pros know about it!

---

### Post by coldraven on 2012-08-05
> BTW: I use a Canon MX310 multifunctional printer/fax/scanner.That's bad news, by coincidence I was just searching for a CISS sytem for my neighbours MX410. They are expensive!! I suppose because the cartridges have the print head attached. They are £90 here in the UK, by comparison a six colour system for my Epson R300 costs just £25 and comes with 600ml of ink.

> If you are printing to "real photos" (for example, a machine at a  drugstore or photo store) then there is a good chance that the machine  is made by Noritsu. Noritsu provides *.icc or *.icm files for its  models, available online. If you don't know the model, search online for  other experiences of the common models. I have done this, and it is  clear that color management was very useful for such machine prints.  Exception: Some machines may "correct" your colors, whether you like it  or not.@rallg, thanks for the tip. I'm going to ask my photo lab what make machine they have and try to get better prints.

---

### Post by Rallg on 2012-08-05
Don't forget that there are also grades of ink. The price of color ink cartridges that are specifically intended for high-end photo printing cost MUCH more than the generic stuff. However, as you noted, in this case the cost factor probably has to do with the non-ink features of the cartridge.

All of this is thoroughly discussed on web sites devoted to cameras and photo printing. That is, unless you are having a software problem, or a problem with the computer-printer interface, the use of color with Ubuntu/Gimp is much the same as it is for Mac/Photoshop or anything else. The *.icc and *.icm files are the same. The meaning of "gamut" and "perceptual" is the same. The only difference AFAIK is that Photoshop and other commercial software can do pre-press color separations in a format acceptable to commercial presses, whereas it's a challenge to do it with Gimp. But you don't need that.

So, to learn more about color, your best bet is to find your way to a site about cameras and printing. Before you do that, learn what the HSV and L*ab color modes do. Wikipedia has a good article on the subject. If you get into serious color adjustments, you may find that it's easier to edit in HSV or L*ab mode than in RGB.

---

### Post by gesti on 2012-08-05
@Rallg, thank you for your help. Now I can start to experiment with papers and inks. :)

> That's bad news, by coincidence I was just searching for a CISS sytem  for my neighbours MX410. They are expensive!! I suppose because the  cartridges have the print head attached. They are £90 here in the UK, by  comparison a six colour system for my Epson R300 costs just £25 and  comes with 600ml of ink.
Yep, it's indeed expensive, but still a lot cheaper then to buy cartages all the time. Two sets of original canon cartage, or four sets of after-market cartages cost the same as one set of this CISS and in ml the CISS is nearly ten times of a normal cartage.

But we're a bit off topic now, so I'll mark the thread as solved.
Once again thank you all for the help and advice!

---

### Post by Rallg on 2012-08-05
I should have done this earlier...

A few posts back, it was noted that softproofing (also known as color proof) was showing large areas of out-of-gamut, depending on the profile used.

I have a photo with some out-of-gamut speckles for a particular *.icc profile. But I've checked that using a non-Gimp program that is professionally used for that purpose.

However, when I looked for out-of-gamut with the same profile, same image in Gimp, Surprise! It showed vast out-of-gamut areas. I double-checked using another method, and it's clear that Gimp is wrong. It tried with several *.icc profiles, so it's not that there is a simple file error in one of the *.icc files.

So I did a web search, and sure enough (over at Flickr) there were reports of excessive out-of-gamut in Gimp.

Thus, it may be that Gimp's softproof feature needs rework.

From the user perspective: Two kinds of color are likely to be out-of-gamut. One kind is intense, saturated bright colors. Those are usually "not found in nature," and if you're photographing something with man-made colors, you'll just have to live with the slightly less saturated color rendition.

The other kind of out-of-gamut are very dark but saturated colors. The reason they are out-of-gamut is because the paper can only hold so much ink in an area; usually it cannot take high doese of all four ink colors. Such out-of-gamut color often appear as speckles in shadow areas. They are unimportant, because you couldn't see much color detail there anyway. Unless you are photogrphic a modern art painting that consists of various shades of off-black, I wouldn't worry about it.

The general consensus among amateur photographers who are not trying to do commercial images for mass-printing is: forget about out-of gamut.

Here's an exercise you can try. DO THIS ON A COPY, NOT THE ORIGINAL PHOTO:

1. Start with a *.jpg image of something that has a mix of very bright and very dark areas. Do not use "print simulation mode."

2. Colors > Components > Decompose > CMYK to produce a new image with four black-and-white layers.

3. In the new image, set the foreground color to 404040 (which is 25% gray). Bucket Fill: Mode=Multiply, Whole Selection. Do this for all four layers.

4. For each layer, change its mode from Normal to Addition.

5. Flatten to one layer. In this image, the lightest areas use the most combined ink, the dark areas use little ink.

6. A cheap ink/paper combination might permit only 60% total ink dose (240 out of 4x100). Let's suppose that you are using that. Then, 60% of 255 (white) would be about 154. Go to Colors > Threshold and set the threshold level to 154.

7. You now have a black-white image (no gray) in which the white areas show places where the color is too deep for the printer. Those spots are out-of-gamut due to ink carrying load.

Note that this method doesn't show areas that are out-of-gamut for bright saturated colors.

EDIT: I did some more searching on the web. Apparently, Gimp has a long history of reporting excessive out-of-gamut when the color is very dark. Don't worry about it.

---

