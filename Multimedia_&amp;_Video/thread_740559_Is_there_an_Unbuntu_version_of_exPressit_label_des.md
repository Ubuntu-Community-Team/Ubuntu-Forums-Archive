---
title: "Is there an Unbuntu version of exPressit label design?"
date: 2008-03-30
forum: Multimedia &amp; Video
---

### Post by trugreg on 2008-03-30
Is there an Unbuntu version of exPressit label design?

---

### Post by mrpixels0 on 2008-03-30
Have you tried the gimp ? or Glabel or Inkscape perhaps they are pretty good and you should be able to make a template with them for CD, DVD's ect.

Note: Installing Wine may also help as it MIGHT be able to install and run it, but this is not a sure fire solution just a possibility.

Hope that helps 
MP0

---

### Post by ubuntu27 on 2008-03-30
You can try [glabels]("http://glabels.sourceforge.net/")

> gLabels is a lightweight program for creating labels, business cards and media
covers for the GNOME desktop environment. It is designed to work with various
laser/ink-jet peel-off label and business card sheets that you'll find at most
office supply stores.

To install, use Synaptic Package Manager or use the folling command in the terminal

```
sudo apt-get install glabels
```

Ok. I see that what you want is to create labels for CD or DVDs. Here are some programs for that:


**kover**

> Kover is a WYSIWYG CD cover printer. You have the ability to enter
the title, contents, set background colors, enter text, embed images
or stream the title and tracks from CDDB (including CDDB Code 211).
Kover can authenticate through a proxy (Basic, but not Digest) for
accessing CDDB, and make a CDDB request just by entering the CDDB ID
(i.e., no need to have the CD inserted).

```
sudo apt-get install kover
```

PS: kover is a kde application. If you are using Ubuntu (GNOME) it will most likely install a some other libraries. Don't worry, it is normal. 

[cdlabelgen]("http://www.aczoom.com/tools/cdinsert/")

> cdlabelgen was designed to simplify the process of
 generating labels for CDs and DVDs. It originated as a program
to allow auto generation of front cards and tray cards for CDs
burned via an automated mechanism (specifically for archiving
data), but has now become popular for labelling CD
compilations of mp3's, and copies of CDs. Note that cdlabelgen
does not actually print anything--it just spits out
postscript, which you can then do with as you please.

---

### Post by wolfen69 on 2008-03-30
glabels is an awesome little app. i use it for labels (uses Avery standard sizes) and business cards.

---

### Post by wolfen69 on 2008-03-30
> **ubuntu27 said:**
> You can try [glabels]("http://glabels.sourceforge.net/")



To install, use Synaptic Package Manager or use the folling command in the terminal

```
sudo apt-get install glabels
```

Ok. I see that what you want is to create labels for CD or DVDs. Here are some programs for that:


**kover**



```
sudo apt-get install kover
```

PS: kover is a kde application. If you are using Ubuntu (GNOME) it will most likely install a some other libraries. Don't worry, it is normal. 

[cdlabelgen]("http://www.aczoom.com/tools/cdinsert/")

thanks for the info. i didnt know about a couple of those.

---

### Post by ubuntu27 on 2008-03-30
I don't remeber that glabels can design CD covers..

Can glabels design CD/DVD covers? I have a feeling that it can...

---

