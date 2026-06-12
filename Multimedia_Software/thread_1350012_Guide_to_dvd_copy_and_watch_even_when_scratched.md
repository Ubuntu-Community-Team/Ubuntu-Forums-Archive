---
title: "Guide to dvd copy and watch even when scratched"
date: 2009-12-08
forum: Multimedia Software
---

### Post by acidviews on 2009-12-08
[I][B][COLOR=DarkRed]Hi everybody well i have a little guide that i would like to share with you on how to copy dvd's that are scratched ! And you can even watch them on ubuntu!

The tools you will need are wine, dvd shrink
dvd decrypter, fixvts and ifoedit.

Start by installing dvd shrink 
[http://www.softpedia.com/progDownload/DVD-Shrink-Download-4128.html](http://www.softpedia.com/progDownload/DVD-Shrink-Download-4128.html)
Configure wine to run as xp with dvd shrink

and dvd decrypter 
[http://www.mrbass.org/dvdrip/](http://www.mrbass.org/dvdrip/)
configure wine to as win N.T 4.0

the ifoedit 
[http://www.videohelp.com/tools/IfoEdit](http://www.videohelp.com/tools/IfoEdit)
and vts fix
[http://www.videohelp.com/tools/FixVTS](http://www.videohelp.com/tools/FixVTS)
small light weight apps which u simply click an runs 
in xp mode


Configure dvd decrypter 
Tools > settings
io tab> check the ignore read errors box
css tab> brute force >io keyexchange and the boxes force vob flag removal
and use key from another file on failure
ifo mode tab> remove rc,rce,puo and vobpuo protcetion
filemode tab> remove protections here aswell

clik ok now for options

Ok now we are ready to start ripping insert dvd into tray open dvd decrypter
Now clik on mode and go to file mode
now a long list should pop up and here we will choose which ones to rip. 

What we are looking for is .vob files in a sequence i.e. VTS_07_0.VOB 
we need to have as many in a row as we can i.e            VTS_07_6.VOB
Plz note they can be labeled anything what we realy need here is a few in sequence.

Right click on the first file Stream Processing and it will then search for
the stream to rip and just press ok to rip. (have patience with scratched dvd's as eventualy you will get what you need).

Rinse and repeat for the files in sequence of files

Now we cheq to see if we have the ENTIRE MOVIE
locate ur files i put mine i.e. /home/myname/Dvd's
and check the the begining and the end of all ya files to make sure it all
makes  sence.(I.E. 02.vob guy in blue shirt in start of 03.vob
(if not look thru ur dvd for the missing one u need to rip)

Ok now this is the most important thing very silly but our dvd maynot
work if we don't do it. We need to rename the file keeping sequence
to VTS_01_0 thru to VTS_01_6.
If like me and you forget u may end up with a nonplaying dvd.
Now having the files is not all there is to do we have to create the
config file for the dvdplayers to know what to play.

Open ifo.exe 
in the bottom near middle clik create ifo
now clik create pgc for each vob
output stream is where the vobs are i.e /home.myname/dvd's
clik middlebox same as sorce
press ok and we have to wait for a lil wile
Once done press save to make sure ,then close

now we have a normal dvd that has no copy protection at all
and we can watch on linux :)

The dvd atm is too big for a normal dvd open up shrink an shrink the files,
if shrink hates you use fixvts.exe to tidy up the files then use shrink
and burn.

*Possible Bug of file's  go missing u need to relog out of ubuntu im not sure 
why this is but relog to get missing files back.

*Menu wont work and previews an copyright crap have all been skipped so
it is only the movie that you are going to watch should auto-play.
sombody else can do this part as im only interested in a working tittle.

I hope this guide works as good for you as it does for me ENJOY!:popcorn:


[/COLOR][/B][/I]

---

### Post by cchester on 2009-12-08
Thanks for the howto.

---

### Post by Supertramp1138 on 2009-12-08
why thank you kind sir:D

---

