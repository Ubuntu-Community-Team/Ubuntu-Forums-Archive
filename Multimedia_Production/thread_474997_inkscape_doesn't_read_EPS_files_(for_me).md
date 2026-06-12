---
title: "inkscape doesn't read EPS files (for me)"
date: 2007-06-15
forum: Multimedia Production
---

### Post by silbar on 2007-06-15
Greetings,

I will soon need to edit some EPS (encapsulated postscript) files -- add labels to graph axes, etc.  Looking for a vector drawing package like Adobe Illustrator I installed Inkscape (on Dapper Drake).  To my amazement (and chagrin) it appears that Inkscape doesn't want to open any *.eps files.  Which is just something that I thought a vector drawing program would prefer to do.  Am I missing some trick here?

   Dick Silbar

---

### Post by kayosiii on 2007-06-17
You will need to install pstoedit....
If you find that you are not getting satisfactory results. The current importer is "brittle".

An alternate path you could use is to import into scribus and save as svg from there.

---

### Post by niceguy123 on 2007-10-07
> **kayosiii said:**
> You will need to install pstoedit....
If you find that you are not getting satisfactory results. The current importer is "brittle".

An alternate path you could use is to import into scribus and save as svg from there.


OK, I installed pstoedit. Now how do I run it?

---

### Post by Foomandoonian on 2008-03-08
> **niceguy123 said:**
> OK, I installed pstoedit. Now how do I run it?

Did you ever figure this out?

---

### Post by Ampi on 2008-04-19
Well, I have pstoedit installed and this is how I use it 

# pstoedit -f "filetype" ~/plot.eps ~/plot.[newextension]

for example if you want to convert: ps -> fig

# pstoedit -f xfig ~/plot.ps ~/plot.fig

But on my computer it runs, but then it never ends....

Any ideas?

---

### Post by graben3 on 2008-05-08
I confirm this problem. 

I have v 0.46 installed
Using Ubuntu Hardy 8.04

Out of the box inkscape did not open .eps files.

I did the following to make it open :

Go into synaptic.

Search for these packages and install them. Also install similar packages (I wanted it to work for sure !)

perlmagick
imagemagick
sketch
libwmf-bin
dia
pstoedit

(Not all these packages are necessary but I prefer to tell what I did to make it work so you can reproduce the same thing

Then if you have troubles opening EPS files containing letters that have a hole in them, just see this :

[https://bugs.launchpad.net/inkscape/+bug/168448](https://bugs.launchpad.net/inkscape/+bug/168448)

Open this file : 
/usr/share/inkscape/extensions/eps_input.inx

Where it is written this :
pstoedit -f plot-svg

replace it by this : 
pstoedit -f plot-svg -mergetext -ssp

This fix the holes problems and some text being in separate letters so difficult to edit.

See the attached files. For me all letters like A, O, e, p, etc.. where not showing the hole in them. The -ssp & -mergetext fixed this in eps files.

Hope this works for you

---

### Post by silbar on 2008-07-15
Greetings,

Update on my posting back on June 15, the start of this thread.  I have since upgraded to Hardy and installed pstoedit.  Using the suggestion by Ampi (actually found elsewhere by googling "pstoedit eps svg"), I can now load an EPS file into Inkscape.  In fact, I believe it isn't necessary for me to do the whole "pstoedit -f plot-svg my.eps my.svg" route, as the open-file option shows EPS files and loads one, albeit with an error message of some kind from pstoedit.  OK, so that's solved.

HOWEVER, my original purpose in doing this was to be able to add some labels to the EPS graph generated, say, by Mathematica.  I am still chagrined to discovery that Inkscape seems NOT to be able to display a Greek letter!  Any Greeks that were in the original EPS have been converted into Roman.  There are two Symbol fonts in the font pull-down menu list, but those ALSO only come out as Roman.  Am I missing something here?

Also, I don't see how to export a finished product from Inkscape into anything execpt a PNG format.  My publishers are expecting submissions with EPS files.  Am I missing something here as well?

What I have had to do, in the absence of a useable Inkscape, is to reconstruct all these graphs from scratch using Grace, which does do the Greeks (and subscripts) and does export into EPS.

Dick Silbar

---

### Post by silbar on 2008-07-16
Update from my posting yesterday: I was wrong about only being able to export to bitmap PNG.  You can choose PS or EPS (among other formats) from the File > Save As panel (at the bottom).

Still, Inkscape isn't useful to me without Greek letters and other symbols, not to mention sub and superscripts.  Hopefully, I just don't know how to get those -- anyone?

Dick Silbar

---

### Post by silbar on 2008-07-16
It also turns out there is a way to get Greeks.  By googling "inkscape greek" I found a (very) old thread in this forum, "Greek letters in Inkscape, Gimp?".  Several good suggestions there -- the one by somosx on 3/16/08 strikes me as the most useful -- adding a Greek keyboard layout to the system.  Go see that thread.

Dick Silbar

---

### Post by silbar on 2008-07-16
OK, probably my last posting in this thread.  I consider my problems with Inkscape now (mostly) solved.

For me, the best way to get Greeks and mathematics into Inkscape is to use the TeX Text extenion, which allows you to enter re-editable LaTeX expressions:

[http://www.elisanet.fi/ptvirtan/software/textext/index.html]("http://www.elisanet.fi/ptvirtan/software/textext/index.html")

It requires installation of an Inkscape extension, but the instructions are all there on the above web page.

Dick Silbar

---

### Post by hugmenot on 2008-07-16
I expect epstopdf or epspdf to work better than pstoedit.
I don't have a good opinion of pstoedit. Once you have PDF Inkscape will do a fair job importing it.

---

