---
title: "isn't there some way to insert a jpg into a pdf???"
date: 2011-06-12
forum: Multimedia Software
---

### Post by ClientAlive on 2011-06-12
I've been all over the internet for the last several hours (at least 3, I lost track). I see the same lousy question coming up over and over. Are people finding a way to do it? It seems so. Are most of the solutions something I think I'm capable of doing? Probably not.

This is crazy! We're trying to fill out a document and sign it between the two of us. He's gotten his part done but he has expensive software that I don't have and can't afford. The whole thing is starting to get a little sour for us both by this point. I've been fussing with this thing for over 3 days now.

I downloaded PDFedit today and was able to use it to fill text into the fields that require that. Now I have one remaining space that needs my signature. I have a jpg file of my sig saved but I'll be darned if I can get the thing into the pdf. Come tomorrow I'll have to go back to work at my regular job and God knows when I'll have time to get back to this. By that time the deal is probably blown!

For the love of God and all that is good doesn't anyone know how to get this accomplished?? PDFedit seems like it should be able to do this but I just don't know how to use it well enough.

Please help!

Thanks for taking the time to read this. I know it isn't the sweetest nicest thing a person could write but I'm just about livid over this whole thing. What ought to be the simplest thing in the world; and, in reality, it's the horror of horrors!

---

### Post by ClientAlive on 2011-06-12
I found the pdf import extension for open office draw but when I open the pdf file in it it is just blank. It doesn't display.
----------------------

Edit: Apparently I can open other pdf documents with it - just not this one. The one stinkin' pdf I need to. It was created in open office word processor and then "export as pdf". Then we've each added of changed things in it. what the hell!

---

### Post by sojyujai on 2011-06-13
I usually edit pdf's in Inkscape.  It works pretty well.  You can add images, text, vector drawings...

The one problem with Inkscape is that it sometimes replaces the embedded fonts in the pdf with system fonts - which can mangle the layout.  At least that used to be a problem, I haven't checked recently.

There's a workaround I use to solve the font problem - first convert the pdf to postscript. The text gets converted to curves and won't be replaced.  You can convert a pdf to postscript using ghostscript with this command:
```
gs -sDEVICE=pswrite -dNOCACHE -sOutputFile=nofont-MyDocument.ps -q -dbatch -dNOPAUSE MyDocument.pdf -c quit 
```

where MyDocument.pdf is the original document and nofont-MyDocument.ps will be the name of the new postscript file.

If you need to you can convert the postscript back to pdf with ps2pdf using this command:
```
ps2pdf nofont-MyDocument.ps nofont-MyDocument.pdf
```

Although Inkscape can open postscript files too, and let you save them in pdf.

---

### Post by ClientAlive on 2011-06-13
> **sojyujai said:**
> I usually edit pdf's in Inkscape.  It works pretty well.  You can add images, text, vector drawings...

The one problem with Inkscape is that it sometimes replaces the embedded fonts in the pdf with system fonts - which can mangle the layout.  At least that used to be a problem, I haven't checked recently.

There's a workaround I use to solve the font problem - first convert the pdf to postscript. The text gets converted to curves and won't be replaced.  You can convert a pdf to postscript using ghostscript with this command:
```
gs -sDEVICE=pswrite -dNOCACHE -sOutputFile=nofont-MyDocument.ps -q -dbatch -dNOPAUSE MyDocument.pdf -c quit 
```

where MyDocument.pdf is the original document and nofont-MyDocument.ps will be the name of the new postscript file.

If you need to you can convert the postscript back to pdf with ps2pdf using this command:
```
ps2pdf nofont-MyDocument.ps nofont-MyDocument.pdf
```

Although Inkscape can open postscript files too, and let you save them in pdf.


Hi,

Thanks for the reply. After I posted this last night I found something that ought to work except it won't display the one pdf I need it to and I don't know why.

I'm one of these guys that knows absolutely nothing about imaging software like gimp and photoshop, etc. I'm not sure what Inkscape is but I assume its like those. Every time I've tried to do something in Gimp, within 5 min I find myself about to go off the deep end with that thing. I've never seen anything so complicated in my life and it takes the liberty of "helping you" with every little thing that really ought to be very simple to do. So I guess what I'm saying is I don't have much hope for any imaging software being something I could do.

What I found last night was something called pdf import extension for open office. It opens the pdf in draw and lets you edit it (including copy paste an image). It opens any other pdf for me, even the original pdf of the document, but it won't display the one where my friend has filled in his information (the one document I need it to). PDFedit will open that document though so I don't understand why/ what is going on. When I open it in draw what I get looks like blank pages.

I wish there were some way to figure out what the problem is with displaying it in draw and use that. It can do everything I need and it's very simple and the features work in a way I am familiar with from using word processors. Do you have any ideas how to figure that out??

---

### Post by sojyujai on 2011-06-13
Sorry, I don't know much about Draw, I've never really used it.  A couple of years ago I went through the same hassle you're going through now - I tired the pdf import for open office - but at the time it just made a mess of things, for me anyway.  I found Inkscape worked pretty well so I just stuck with it.  I've never used PDFedit.  

I have no idea why your edited pdf won't import into open office - it sounds like the editing did something to make it incompatible with the pdf import for oo.  Was the edited pdf saved in a higher pdf version number than the original?  It could be that the oo pdf import only works with early pdf versions - but I'm only guessing.

Inkscape is a vector graphics (drawing) program along the same lines as Open Office Draw. It's not an image editor like the Gimp or Photoshop.  I use it regularly for filling in text forms and adding my signature to pdfs.  Sure there's a learning curve to use it but I found it fairly intuitive.  It's free software so all it costs to try it is a few minutes of download time :)

---

### Post by ClientAlive on 2011-06-13
> **sojyujai said:**
> Sorry, I don't know much about Draw, I've never really used it.  A couple of years ago I went through the same hassle you're going through now - I tired the pdf import for open office - but at the time it just made a mess of things, for me anyway.  I found Inkscape worked pretty well so I just stuck with it.  I've never used PDFedit.  

I have no idea why your edited pdf won't import into open office - it sounds like the editing did something to make it incompatible with the pdf import for oo.  Was the edited pdf saved in a higher pdf version number than the original?  It could be that the oo pdf import only works with early pdf versions - but I'm only guessing.

Inkscape is a vector graphics (drawing) program along the same lines as Open Office Draw. It's not an image editor like the Gimp or Photoshop.  I use it regularly for filling in text forms and adding my signature to pdfs.  Sure there's a learning curve to use it but I found it fairly intuitive.  It's free software so all it costs to try it is a few minutes of download time :)


Right on. I appreciate your effort. I was kinda freaking out over this last night. If it was just me hassling with it, it would be one thing but in this case it was another person as well - putting up with my hassle I mean.

So I got my immediate issue resolved and I learned something about dealing with pdf. PDFedit, I think, is pretty robust software (and it's foss). I don't think it can insert an image though. PDF Import is very simple to use. Actually its just an extension (but you know that) so its just using draw really - and that's a cinch.

I figured I needed to create a copy that has all my info filled into it (with signature) and ready to go. Then, when I need to use it, I can just fill in the text for the general part at the top and send it to the other person for them to do theirs.

I hate to say it but I think I'll make sure I go first after this.  :D

My friend runs Windows and uses some kind of expensive Adobe software for adding a signature. I suspect that's what caused my troubles with that document. When I did it that way I described above (going first) he didn't have any trouble doing his with whatever software he uses.

So now I know that I can start off with the open office draw with its extension and if the other person does have trouble on their end I can suggest they dl open office draw and the extension. In a case like that we would both be using the same software for it and there's really no reason for there to be a problem. Open Office works with Windows and Linux too so that's a plus.

Yeah, I think I found my solution. Scary, I sound like a commercial. I'm just happy to have figured something out that works though.

Be Blessed.

Jake

---

