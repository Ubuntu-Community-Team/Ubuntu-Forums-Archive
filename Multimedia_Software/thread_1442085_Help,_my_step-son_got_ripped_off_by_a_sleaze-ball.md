---
title: "Help, my step-son got ripped off by a sleaze-ball"
date: 2010-03-29
forum: Multimedia Software
---

### Post by Eathray on 2010-03-29
So my step-son got married, big wedding, this and that...

Enter the shady, sleaze-ball, rip-off artist photographer, promising the full package with photo album for $3700.00, then giving only the $1500.00 package after holding the pictures ransom, no album, only a quarter of the pictures, and a read-only disk.

So now that the kids have been ripped off for $2200.00 dollars, how do I take this read-only disk and make the photos accessible so they can make the photo album they paid for but didn't get?

I know that's not much technical info, so let me know what you need to know. Using Ubuntu 9.10, and the images appear to be jpegs, but are locked. Tried moving one to the hard-drive and renaming, but still can't open.

Thanks in advance.

Eathray

---

### Post by nothingspecial on 2010-03-29
Have you tried using sudo chmod to change the permissions on the files.

Or sudo chown to change ownership.

---

### Post by lavinog on 2010-03-29
> **Eathray said:**
> So my step-son got married, big wedding, this and that...

Enter the shady, sleaze-ball, rip-off artist photographer, promising the full package with photo album for $3700.00, then giving only the $1500.00 package after holding the pictures ransom, no album, only a quarter of the pictures, and a read-only disk.

So now that the kids have been ripped off for $2200.00 dollars, how do I take this read-only disk and make the photos accessible so they can make the photo album they paid for but didn't get?

I know that's not much technical info, so let me know what you need to know. Using Ubuntu 9.10, and the images appear to be jpegs, but are locked. Tried moving one to the hard-drive and renaming, but still can't open.

Thanks in advance.

Eathray
He gave you a cd?

When you say locked, you mean that you cannot open the files, correct?
when you say they appear to jpegs, how are you determining this...is it possible that they are raw files...in which case there should be a package to make them readable.
How big are the files?

A neat tool in linux is the file command
open a terminal
cd to the drive (assuming it is the cd drive):
```

cd /media/cdrom

```
if cdrom doesn't work it might be cdrom0
use ls to list the filenames
post what this command reports
```

file *

```

---

### Post by Eathray on 2010-03-29
nothingspecial,

Thanks. Can you tell me, the photos are on a cd. do the sudo commands you mentioned need to contain that? Just open a terminal and it will know I'm talking about the disk in the cd-rom?

---

### Post by nothingspecial on 2010-03-29
It might be easier to type ```
gksudo nautilus
``` and go to the cd in the file browser.

Then copy the contents to your desktop.

Rather than go into the cd itself.

---

### Post by Eathray on 2010-03-29
Thanks.

Can you dumb it down a little for me? Once I enter the nautilus command, I leave the terminal, and drag/drop the cd files to the desktop?

Then I open a new terminal and run the ch commands, and it will recognize the files on the desktop are meant?

Sorry. I've come a long way with Linux, but this area is new to me :)

Eathray

---

### Post by nothingspecial on 2010-03-29
If you enter the command, a new file browser will open.

Right click the folder in the cd (in the new file browser ( if there is no file containing all the jpegs click one of them (once) then press Ctrl+A to highlight them all, then right click) and choose copy.

Then, still in your new file browser find your Desktop (located in your home directory) and go to it. Right click in it and choose paste.

chown and chmod on their own will not work but I cannot give you the full commands until I know what the files are called or they are on your Desktop.

*****(Putting them on your Desktop is not strictly necessary but let`s keep this simple)*****

---

### Post by Eathray on 2010-03-29
k, working on it... be right back.

---

### Post by Maheriano on 2010-03-29
This sounds like fun actually. You could try booting into a DOS machine and copying them that way. Software restrictions only work on software that supports the restriction type.
Why don't you just make the photographer give you what you paid for? Wouldn't that be easier?

---

### Post by nothingspecial on 2010-03-29
> **Maheriano said:**
> This sounds like fun actually. You could try booting into a DOS machine and copying them that way. Software restrictions only work on software that supports the restriction type.
Why don't you just make the photographer give you what you paid for? Wouldn't that be easier?

I`m hoping this is just a linux/windows permissions problem.

If not...........

---

### Post by Eathray on 2010-03-29
okay, the nautilus command gives errors, but opens the window like you said. I copied and pasted the containing file to the desktop, but it didn't create an icon on the desktop, so I dragged and dropped the containing file to the desktop, and it copied there.

---

### Post by nothingspecial on 2010-03-29
So, what do you have?

Post the output of

```
ls ~/Desktop
```

remember - I need to know what the file is called.

---

### Post by Eathray on 2010-03-29
File is called:

flip 2_opt_files

and command gave that name, as well as other desktop icons like firefox, etc.

---

### Post by nothingspecial on 2010-03-29
Try```
 sudo chown -R username:username ~/Desktop/flip\ 2_opt_files/
```

and

```
sudo chmod -R 755 ~/username/flip\ 2_opt_files
```

Change each instance of username (2 in the first and 1 in the second) to your actual username.

Can you view the photos?

---

### Post by Eathray on 2010-03-29
On the chown command, says the sudo commands in universe and main are not found... trying the other one... be back

---

### Post by nothingspecial on 2010-03-29
What??????


Unless there is sensitive data on your Desktop, post the results of ```
ls -l ~/Desktop
```

I understand completely if you don`t want to. :p

---

### Post by lavinog on 2010-03-29
Can you get us a listing or a screenshot of what you see?
CDs do not have permission bits that I know of so I don't think chmod/chown will help in this matter.  You haven't given specific details about the issue.  I can't tell what you mean by locked...normally locked means a permission issue, but you should get a specific error about you not having permission if this was the case.

---

### Post by Eathray on 2010-03-29
chmod just says invalid option.

If it helps, I'm positive this disk is secured somehow... the $%@! photographer said it was only viewable as a slideshow.

---

### Post by Eathray on 2010-03-29
No, no sensitive data (haha) happily married here!

I've been going back and forth between my laptop and my step-kid's computer. Stand-by, I'll log out of this a sign in on his so I can give you snapshots.

p.s. I am getting permissions errors mostly, as one of the others mentioned.

---

### Post by nothingspecial on 2010-03-29
That may be true, have alook back through the thread.

I`ve given a couple of other things to do like 

```
ls -l ~/Desktop
```

and lavinog has requested a screenshot. If these photos have been encrypted (or locked or whatever) by some specific software, then unlocking them might be (nearly) impossible.

The fact that they are .jpgs gives me hope.

---

### Post by Eathray on 2010-03-29
Okay thanks man... I'm going to hunt the thread like you say and catch up with the others

appreciate yer time

---

### Post by lavinog on 2010-03-29
> **Eathray said:**
> chmod just says invalid option.

If it helps, I'm positive this disk is secured somehow... the $%@! photographer said it was only viewable as a slideshow.

ahh.
There must be a program you need to install...it's likely to be a windows only program so you will need to install wine.

do you see any files that end in .exe?

If the slideshow is the only way to view the files, then the files must be encrypted...it might be possible that someone has broke the encryption.

Also if the images can be displayed as a slideshow you could do a screengrab...It might also be possible to setup a virtual desktop of a larger size than your resolution to get a high res screengrab.
(the prtsc key does a screen capture)

---

### Post by nothingspecial on 2010-03-29
It`s only a couple of posts.


I want to help you before I "have" to go to sleep.

We need to know if this is a permissions, or a software issue.

---

### Post by lavinog on 2010-03-29
I don't know about your location, but you may want to take this guy to small claims court...Most likely he will follow through with the deal when he gets a court summons.

---

### Post by nothingspecial on 2010-03-29
Thankfully, 11 years ago when I got married, the photographer was only a couple of hundred quid.

My godmother`s husband is a keen amatuer photographer. He came to the wedding.

In that day, I don`t know how it is now, we paid the photographer £20 to turn up and do the photos.

But to buy them would have been £700+

My godmother`s husband`s photos look great in our house ;)

---

### Post by Eathray on 2010-03-29
maheriano,

no, wouldn't be easier. The only way we can get anything more out of the d**k-weed photographer is to take him to court, and the most the court can make him do is make him give back the money... but we don't want the money, we want the photos. The wedding's over, so we can't take more.

Everything we need is on this damn disk. we can make our own album if we can just get it open. Then maybe we'll hit him in court after for the extra $2200.00 the kids lost, but we want to open this disk first, because what if he has an 'accident' with his copies when he finds out we're taking him to court? Bottom line, the pictures can't be replaced; we'd have to do another wedding!

---

### Post by nothingspecial on 2010-03-29
> **Eathray said:**
> maheriano,

 Bottom line, the pictures can't be replaced; we'd have to do another wedding!

I agree.

Therefore, can you get one jpg (to try with) using gksudo nautilus somewhere - Desktop, your home folder, anywhere really. 

If we can view one, we can view them all.

But I am going to *****have*****!!!!! to go to bed soon...........

---

### Post by Eathray on 2010-03-29
Okay, Lavinog,

sorry, you guys are quick and I'm getting old ;) see my last remark on court. It's an option, but I'd rather get into the disk first.

I'm almost positive I saw an exe file somewhere... I'll check and get back to you.

---

### Post by Eathray on 2010-03-29
nothingspecial,

It's okay, partner, get some sleep. This thread will be here till this disk is successfully hacked. I'll catch up with you tomorrow, but please come back.

thanks again. see you tomorrow.

Eathray

---

### Post by Chronon on 2010-03-29
Maybe some of the tools [here](https://help.ubuntu.com/community/DataRecovery) can help.

---

### Post by Eathray on 2010-03-29
Lavinog,

okay, in the cdrom0 file browser, there is a file under the containing folder called: startCD.exe

Also, I found another file called: Flip 2.opx

The opx file contains all kinds of info. The program used to create the cd is called EbooksysVersion 1.40. There is a unique identifier key, and a separate key for all 386 pictures. I'm guessing this file would not be visible in Windows :P  Anyway, I think this may be the motherload in gaining access to the disk. I'm going to read it carefully... any suggestions how I should use this info or what I should be looking for in this file? It seems to contain all the permission keys, but I'm not sure yet how to use them.

thanks

---

### Post by Eathray on 2010-03-29
Thanks Chronon, I'll check it out. Also, check my previous post to this one about the .opx file I found and tell me what you think.

thanks

Eathray

---

### Post by blur xc on 2010-03-29
Maybe I'm missing something but as far as I know, CD's are read only media, aren't they?  So what good is it to chown and chmod files on the cd?  I mean, sometimes you can create multi session cd's, but I doubt the photog did that, and every time I've done that they only work on the computer they were created on.

Why can't the jpg's  be copied off of the cd to your hard drive again?  

BM

---

### Post by lavinog on 2010-03-29
> **blur xc said:**
> Maybe I'm missing something but as far as I know, CD's are read only media, aren't they?  So what good is it to chown and chmod files on the cd?  I mean, sometimes you can create multi session cd's, but I doubt the photog did that, and every time I've done that they only work on the computer they were created on.

Why can't the jpg's  be copied off of the cd to your hard drive again?  

BM

Basically, the photographer used DRM to prevent them from accessing them with linux, or printing and copying them with anything.

---

### Post by Eathray on 2010-03-29
Blur xc,

check my reply #31. I found a file with the encryption keys for all the pictures. Now I just need to figure out how to use it. 

Thanks and get back to me.

Eathray

---

### Post by lavinog on 2010-03-29
> **Eathray said:**
> Lavinog,

okay, in the cdrom0 file browser, there is a file under the containing folder called: startCD.exe

Also, I found another file called: Flip 2.opx

The opx file contains all kinds of info. The program used to create the cd is called EbooksysVersion 1.40. There is a unique identifier key, and a separate key for all 386 pictures. I'm guessing this file would not be visible in Windows :P  Anyway, I think this may be the motherload in gaining access to the disk. I'm going to read it carefully... any suggestions how I should use this info or what I should be looking for in this file? It seems to contain all the permission keys, but I'm not sure yet how to use them.

thanks

How did you find this photographer?  Maybe you can make sure he doesn't get another photography job again.
Did you get a receipt from him?

well for starters you should be able to install wine from the software center. Once that is installed you should be able to start that startCD.exe file (wine allows that to load)
try that and see how it goes.

the key for each picture is likely to be an encryption key...since each jpg has a magic header, there might be a way to use that information to break the encryption...but I have never tried that before, so I don't know how successful it would be.

---

### Post by Eathray on 2010-03-29
Be back in a bit, guys... I gotta help my youngest with his French lesson.

Anything you think of, please post it. I'll peruse it in just a little while.

Thanks to all of you.

Eathray

---

### Post by blur xc on 2010-03-29
> **lavinog said:**
> Basically, the photographer used DRM to prevent them from accessing them with linux, or printing and copying them with anything.

Ok- I re-read the op, and that freakin' sucks...  

I got an ecrypted pdf e-book for work.  The stupid thing will only open on the computer on which it was originally opened.  Which is fine, unless I'm working at a different computer!  So, I printed it, and scanned it back, but this loses all the search-able text, table of contents, hyper links, etc...  sucks.

Good luck- 
Sue that photog...

BM

---

### Post by lavinog on 2010-03-29
> **blur xc said:**
> Ok- I re-read the op, and that freakin' sucks...  

I got an ecrypted pdf e-book for work.  The stupid thing will only open on the computer on which it was originally opened.  Which is fine, unless I'm working at a different computer!  So, I printed it, and scanned it back, but this loses all the search-able text, table of contents, hyper links, etc...  sucks.

Good luck- 
Sue that photog...

BM

There used to be a trick to modify the ghostscript settings to where printing would make an exact copy without the drm.

---

### Post by lavinog on 2010-03-29
Did the photographer give you a receipt or invoice of any kind?
How did you find him?

---

### Post by solar george on 2010-03-29
Maybe you could post a copy of that file? And if you don't mind one of the encrypted photos as well?

Good luck.

---

### Post by lisati on 2010-03-29
Edit: never mind, highly useless post deleted

---

### Post by bpalone on 2010-03-29
I am assuming you have access to a Windows machine.  If so, check [http://www.flipalbum.com/fahome/store/]("http://www.flipalbum.com/fahome/store/"), they offer a 30 day trial.  It appears this is what it was created with.  They also offer a professional version, which may also have a trial.  The trial might allow you to save without the encryption.

Hope this helps a bit.

---

### Post by babarosa on 2010-03-29
People,

are you sure you aren't helping someone to crack data which he shouldn't have access to (photos of his wife and the gardener, evidence of a murder he is blackmailed for, going to the toilets in his neighbours' garden, ...)?

Who does pay $3.700 for marriage photos, since most matrimonies are getting divorced a few years later?

The OP should contact a consumer consulting service or a lawyer.

I am not kidding!

---

### Post by lavinog on 2010-03-29
> **babarosa said:**
> People,

are you sure you aren't helping someone to crack data which he shouldn't have access to (photos of his wife and the gardener, evidence of a murder he is blackmailed for, going to the toilets in his neighbours' garden, ...)?

Who does pay $3.700 for marriage photos, since most matrimonies are getting divorced a few years later?

The OP should contact a consumer consulting service or a lawyer.

I am not kidding!

A lot of people spend a bunch of money on a photographer...Do you know how much money is spent on weddings?
Who puts evidence of a murder in a slideshow program???

The current issue is that the OP has a cd with images in a proprietary format and a program designed for windows included on the disk.  I cannot see any legal issues with offering help to get the program working on Ubuntu.

---

### Post by Eathray on 2010-03-29
Lavinog,

The bride's family found him. We didn't like him because he was about 20% higher than others in our area, but, the bride wanted perfect pictures... ah well.

---

### Post by MCVenom on 2010-03-29
> **babarosa said:**
> People,

are you sure you aren't helping someone to crack data which he shouldn't have access to (photos of his wife and the gardener, evidence of a murder he is blackmailed for, going to the toilets in his neighbours' garden, ...)?

Who does pay $3.700 for marriage photos, since most matrimonies are getting divorced a few years later?

The OP should contact a consumer consulting service or a lawyer.

I am not kidding!
*facepalm*

...Get out. Just get out man :p

It's a ridiculous suggestion. And if it really is photos of his/her spouse with someone else, more power to them. But I trust the OP. :p

---

### Post by Eathray on 2010-03-29
barbarosa,

Murder? Wow, man. We don't even have a gardener.

The pictures on this disk are paid for. There are receipts. They are the pictures to be used for the imaginary album that was never made, so contractually, they can be used for that purpose. It took a shout-fest in the guy's shop just to extract the cd part of the contract from the prick. It probably will become legal for the $2200.00 over-charge I already mentioned. Giving us this encrypted disk was just this guy's way of giving us the finger as we left.

Anyways, the subject at hand is getting our pictures accessible for an album that's been bought and paid for, but not delivered. 

Conspiracy theories are fun when it's the Kennedys, but not when it's your step-son's wedding.

---

### Post by lavinog on 2010-03-29
did you try what I mentioned about wine?

You can install it by clicking this link: [apt://wine](apt://wine)
(assuming you are using a recent version of ubuntu.)

---

### Post by Eathray on 2010-03-29
BlackOtaku,

Thanks for the defense... I didn't know I was going to get accused of murdering the gardener for sleeping with my wife... wow. All that from a wedding disk. What if it had been a blu-ray? :)

---

### Post by Eathray on 2010-03-29
lavinog,

We're going to try it tonight. We got wine installed on on my step-son's machine a little while ago. I'll report tonight or in the morning if it's too late.

Thanks.

Eathray

---

### Post by lyall on 2010-03-29
OPX File Extension see [http://www.fileinfo.com/extension/opx]("http://www.fileinfo.com/extension/opx") and File Extension OPX at 
[http://filext.com/file-extension/OPX]("http://filext.com/file-extension/OPX")

the last site says Other applications associated with file type OPX
that MS Powerpoint can open
so try Open Office Presentation, it is worth a try

good luck and have fun learning

---

### Post by Eathray on 2010-03-29
lyall,

OpenOffice, we can do that. Thanks for the tip.

Eathray

---

### Post by lavinog on 2010-03-29
> **lyall said:**
> OPX File Extension see [http://www.fileinfo.com/extension/opx]("http://www.fileinfo.com/extension/opx") and File Extension OPX at 
[http://filext.com/file-extension/OPX]("http://filext.com/file-extension/OPX")

the last site says Other applications associated with file type OPX
that MS Powerpoint can open
so try Open Office Presentation, it is worth a try

good luck and have fun learning
The first site says that too, but also mentions that it can also be for the flipalbum application...which we are pretty sure that this is the case here.

it did say this though:
> 

NOTE: Sometimes OPX files can be opened by different versions of FlipAlbum by changing the file extension from ".opx" to ".opf."

Don't know if it would be useful or not, but good to know if we run out of ideas.

---

### Post by Eathray on 2010-03-29
Lavinog,

Okay, Wine does indeed make the disk play. The family is in the back room laughing their heads off at the picture show.

Now, all we need to do is figure out a way to strip these photos out (nothing but the slideshow works, naturally), and stick 'em on a flash drive or something and head for Walmart. I feel like that photo album is almost within reach. Thanks guys.

Please keep your suggestions coming. We're trying each one.

Eathray

---

### Post by Eathray on 2010-03-29
lavinog,

you're correct, it is indeed a flip album.

I'm going to take a bit and look at those .opx links.

---

### Post by lavinog on 2010-03-29
can you output the size of the files?

this command lists the files with human readable file sizes:
```

ls -lh

```

What you are looking for are a bunch of files that are greater than 1M.  Pictures with smaller sizes are likely to be of low quality (1M is 1000k)

---

### Post by Eathray on 2010-03-30
lavinog,

It didn't really show me anything other that icons and wallpaper photos. Nothing that looked like it was from the disk.

---

### Post by Brandel Valico on 2010-03-30
> Getting pictures out of FlipAlbum
October 21, 2005 &#8212; GJ

A couple of friends of mine got married recently, and their photographer sent them their proofs on a CD. He used some product I&#8217;d never heard of, FlipAlbum, that places encrypted versions of the JPEGs on the CD, and includes a (gaudy) viewer to see the pictures.

When it comes to computers and being prevented from my natural behaviour (e.g. distributing to friends and family), I get irritable and a little obsessed. After getting an image of the CD, I picked through it, curious what was done. It&#8217;s pretty clear that the encryption is reversible &#8211; the CD has some encryption keys in a file for the viewer program to use. However, I didn&#8217;t have much interest in taking the direct approach to try my hand hacking the code or anything similarly &#8220;glamorous&#8221;.

I still wanted the pictures though, if only because it was being denied. So I went with a low tech solution.

First, I used Bulent Screen Recorder to record a movie of my desktop. BSR has a useful feature where it records a frame only when the monitored area changes. I killed my windows shell, bb4win, to get an empty blackness on one of my monitors and configured BSR to watch that half of my desktop. I then used FlipAlbum&#8217;s automatic full-screen slideshow to display all the pictures. I ran that overnight at a rate of three seconds per image, recording an uncompressed movie. I had to give three seconds instead of one, as BSR needed a couple seconds to switch to a new file when the current AVI file got too big (1GB).

Next, I used mplayer to extract each frame to a JPEG. I actually used a Win32 port of mplayer, because I was too lazy to upload the movies to process on my Linux server. The win32 version didn&#8217;t have support for non-lossy image types (e.g. PNG), so I bumped the quality to 100.

The next step was to shave off the watermarks BSR embeds into each frame. Fortunately, the pictures weren&#8217;t big enough to fill the whole screen, so the watermarks appeared in the &#8220;dead&#8221; black areas of the image. I looked a little into what Gimp and IrfanView, the desktop graphic programs I most often use, could do for me&#8230; but in the end used ImageMagick. Again, I did it in Windows, using the version that comes with Cygwin.

One little note about ImageMagick (I was using convert and mogrify): I struggled with it a bit, because I was getting a weird result using -shave 50x0 -fuzz 5% -trim. I would end up with pictures that still had empty space to the right and bottom. Using -crop 0x0 had the same effect. I finally figured out that shaving pixels off the left and right side changed the data, but didn&#8217;t change ImageMagick&#8217;s idea of how big the picture was. Transforming the JPEG in two steps, -shave 50x0 then -fuzz 5% -trim, gave the desired result. In case there are purists wondering, the pictures are only proofs, so encoding them a few extra times doesn&#8217;t make much of a difference, especially since the intermediate steps were at 100% quality.

It was fun, and I got to know some useful tools better. From a moral standpoint, I don&#8217;t feel it&#8217;s wrong: the quality of the original pictures provided are too low to blow up even to a 4&#8243;x6&#8243; photo, and the photographer hasn&#8217;t provided the digital touchups yet. It&#8217;s an unnecessary measure that forces people to burn and distribute CDs. How did this protection measure accomplish anything but waste people&#8217;s time taking the long way around?

It makes me nervous for you that he says the images are just proofs and not the RAW image files. If you can't even make a decent 4x6 then your not going to be able to make a decent photo album.

---

### Post by Brandel Valico on 2010-03-30
The FlipAlbum encryption does not seem to affect the image part of a jpeg file, changes in the header of the jpeg file are the reason that you can not open it. To be able to decode the jpef file you have to edit all the files with a hex editor (e.g. Hex Workshop v5, free trial at [http://www.bpsoft.com/](http://www.bpsoft.com/)) and replace the header of the encrypted jpg file with a header of any other (not encrypted jpeg file.
Open the FlipAlbum encrypted jpg file in Hex Workshop and use edit-find (or ctrl-f) to find the first occurrence of the hex value &#8220;FFD9&#8221;, this is the marker that marks the end of the jpeg header. Delete everything from the beginning to the first occurrence of &#8220;FFD9&#8221;. Then open another (not encrypted) jpg photo file you have and copy the the part from the beginning to the first occurence of the hex value &#8220;FFD9&#8221; and then paste this at the
beginning of the encrypted jpeg file in Hex Workshop (make sure the header part ends with only one time &#8220;FFD9&#8221;wink. Save the now no longer encrypted file and then you will be able to open it with photoshop. Upon opening the formerly encrypted files photoshop may claim the files may be broken but is does open the files and they appear to be just perfect. Good Luck!

*******
Looked into this some more. It seems this may help also. At least it may give those with more knowledge then me an idea for how to help you

**********

each CD has its own key. This key is unique and can&#8217;t be put on a key gen, for exemple. The worst is, once encrypted, cannot be decrypted... its just like md5().So, what you got to do is, find the key and use it to open the pic into a html doc. and THAN save it. Each pic usually is around 1.5MB. How? There is a file on your CD which have xhtml where you can find the 'address' for those encrypted pics location. This is the only way I found to get the original pics ( so far, I&#8217;m still working on it ). But anyway, FlipAlbum changes a line of the picture which your computer needs to read and change it with encrypted codes causing it to not load. You can see it yourself if you open a pic you took with Notepad. You&#8217;ll see de digital sign of your camera, time, day, etc AND info like colorset, pallet, blabla, blabla... Try to remove that info to see what happens smiley By now, I think you already have an idea what I&#8217;m talking about...

---

### Post by lavinog on 2010-03-30
> **Eathray said:**
> lavinog,

It didn't really show me anything other that icons and wallpaper photos. Nothing that looked like it was from the disk.

Try this command in a terminal:
```

du -ah /media/cdrom

```
This assumes the cd is in the drive.

---

### Post by lavinog on 2010-03-30
> **Brandel Valico said:**
> The FlipAlbum encryption does not seem to affect the image part of a jpeg file, changes in the header of the jpeg file are the reason that you can not open it. To be able to decode the jpef file you have to edit all the files with a hex editor 

hmmm...I wonder if there is a program that can repair jpeg headers automatically.

I also wonder if photorec (part of the testdisk package) would be able to extract the photos from the disk.

---

### Post by lavinog on 2010-03-30
I found a tool called recoverjpeg
install it here: [apt://recoverjpeg](apt://recoverjpeg)

```

cd /tmp
mkdir photos
cd photos
sudo recoverjpeg /dev/cdrom1
nautilus .

```
I don't have a flipalbum cd to try this with so I don't know if it will work.
also not all computers use /dev/cdrom1  It could be /dev/cdrom0

---

### Post by blur xc on 2010-03-30
> **babarosa said:**
> 
Who does pay $3.700 for marriage photos, since most matrimonies are getting divorced a few years later?


First off- Are you married?  You sound like one of those bitter cynical types...

And 2ndly- the wedding photos are of the most important things at a wedding.  What else from that day do you get to take with you and keep for the rest of your life?  The dress?  It'll sit in a closet never to be worn again.. Maybe by the daughter for her wedding- just maybe.  The cake?  It'll rot.  We kept a piece of ours in the fridge for a few years and then tossed it.  The DJ?  Don't think so...  or how about the booze?  It'll end up vomitted all over the bathroom floor.  

The wedding photos are the only real thing that you get to keep for years and years after the wedding.  It would be foolish to blow tens of thousands of dollars on the processions and reception, and then skimp on the photographer.

My $.02

BM

---

### Post by Eathray on 2010-03-30
lavinog,

Okay I installed that app and ran the code, here's what it said:

[I](nautilus:3749): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
dean@dean-desktop:/tmp/photos$[/I]

Don't know what it means, but obviously it couldn't do what it wanted to do.

eathray

---

### Post by lavinog on 2010-03-30
> **Eathray said:**
> lavinog,

Okay I installed that app and ran the code, here's what it said:

[I](nautilus:3749): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
dean@dean-desktop:/tmp/photos$[/I]

Don't know what it means, but obviously it couldn't do what it wanted to do.

eathray

this error is normal with nautilus:
```
(nautilus:3749): Eel-CRITICAL **: eel_preferences_get_boolean: assertion `preferences_is_initialized ()' failed
```
It will show up whenever you call nautilus from the command line, but it shouldn't prevent it from loading.

did recoverjpeg do anything?

---

### Post by vincentertainment on 2010-03-30
A few thoughts.... 
You said the pics appear to be jpgs. Have you confirmed this? Do the files have a .jpg file extension? Raw files would have other extensions. If he gave you raw files, those are better files once you know how to import them.
 
Do you have a written contract with the photographer? and do you have written copyright release consent?
 
If so, you could file a complaint with the Better Business Bureau for free. If he doesn't resolve the complaint, he will have a harder time landing future gigs. 
 
If you don't have written copyright release consent, and you find a lab that will print these pics for you without it and he were to find out, the photographer could potentially sue you and/or the photo lab.
 
I've worked 8 years in photofinishing and I've been doing photoshop work for about 15 years. photography even longer.

---

### Post by pickarooney on 2010-03-30
Shoot me for being pragmatic but for something this important would you not just put the CD on a Windows PC, get them printed and be done with it?

---

### Post by lavinog on 2010-03-30
> **vinsect said:**
> A few thoughts.... 
You said the pics appear to be jpgs. Have you confirmed this? Do the files have a .jpg file extension? Raw files would have other extensions. If he gave you raw files, those are better files once you know how to import them.

Considering the OP mentioned that there are 380+ photos on a disk I am thinking that they are not RAW files.
>  
If so, you could file a complaint with the Better Business Bureau for free. If he doesn't resolve the complaint, he will have a harder time landing future gigs. 

Unfortunately I don't know if people who shop for wedding photographers check the BBB, but it shouldn't hurt to do it.


The main thing is paperwork...if there is no receipt and no contract it becomes his word vs yours, and I don't know how that will play out in court.

Is the photographer even giving you an option to purchase prints?  Does the cd have a button that provides a way to purchase prints?

---

### Post by lavinog on 2010-03-30
> **pickarooney said:**
> Shoot me for being pragmatic but for something this important would you not just put the CD on a Windows PC, get them printed and be done with it?
I don't think that is the issue.  Windows would have the same issue...the photographer gave them a disk with images that are encrypted.

---

### Post by Eathray on 2010-03-30
vinsict,

We have a contract for the album which was never completed as part of the package. After a shout match, the disk was given in it's place for the purpose of making our own. Everything's legal on our end but not his. As I said before, it's probably going to go legal for his part of not fulfilling his contract. Yes, of course, we're going to talk to the better business bureau, the chamber of commerce, and anyone else we can think of.

---

### Post by jward3010 on 2010-03-30
Ya what?!

---

### Post by Eathray on 2010-03-30
pickaroony,

The pics cannot be copied or printed on any platform. This is the deal, accessing them. They're in a locked format.

---

### Post by Eathray on 2010-03-30
lavinog

It opened a window, but didn't seem to want to do anything beyond that. I'm going to try it again. I restarted the machine.

---

### Post by lavinog on 2010-03-30
> **jward3010 said:**
> Ya what?!

???

---

### Post by nothingspecial on 2010-03-30
[Useless Post]

How are you doing Eathray? Just wanted you to know that I`m still checking this thread, although, as the details emerge, it seems out of my area of knowledge.

If I do come up with anything though, I`ll send it this way.
[/Useless Post]

---

### Post by Eathray on 2010-03-30
nothingspecial,

Thanks man. I appreciate every thought... except maybe the guy who thinks I murdered my gardener... still don't quite get that reply...  :)

---

### Post by Eathray on 2010-03-30
lavinog,

I can only guess jward 3010 is referring to the price of the shady photographer's pics.

On recoverjpeg, it appears to open a window, but it's the file manager, not it's own window. It goes to a default folder called albums, but does not offer any options there or when I navigate to the pics on the disk. doesn't seem to be working. I guess either it won't work for this application, or it's missing a dependency. I can't find it as an actual program under applications or places. Is there a terminal command that launches it, or does something more to make it functional?

eathray

---

### Post by 2hot6ft2 on 2010-03-30
I take it you have already tried PrintScreen and Record My Desktop to capture the images as the slide show is played to no avail. there may be a way to do it with FFmpeg which may capture it, then the pics. could be saved to individual files using VLC or MPlayer to play the recorded mkv file and using Take Screen Shot which would let you crop them at the same time that you save them.

While it's no where near as much fun as cracking the contents of the cd it may be easier. And there would be a loss of quality I'm sure but what can you do.

Why do I think this may work if PrintScreen and Record My Desktop wont is best said by quoting so this:
> **mocha said:**
> I've been using this method and it works really well for grabbing videos from webpages that can't be grabbed in any other way.  You can add "-t hh:mm:ss" to limit the capture time for unattended recording.

So if you want to try it I'll give a short version of a how to and the source of where I got the instructions and everything from so you can modify it to suite your needs like defining the screen capture area which would help improve the quality of the capture.

I have it set to record my entire desktop which is 1366x768 and then took a screen shot of this reply box (using Take Screenshot > Select area to grab) while pausing it in VLC Player and it looked pretty good.
I used gnome-screenshot which can be installed from the repos thru Synaptic or by using
```
sudo apt-get install gnome-screenshot
```
and will then be in
Applications > Accessories > Take Screenshot
if you don't already have it.

This is the source of the info on installing and using FFmpeg
[HOWTO: Proper Screencasting on Linux]("http://ubuntuforums.org/showthread.php?t=1392026") 
Which is where you can find out how to define the area to capture in Step 1.

This is where I found the short way to install the codecs.
[HOWTO: Easily enable MP3, MPEG4, AAC, and other restricted encoding in FFmpeg]("http://ubuntuforums.org/showthread.php?t=1117283")

So all props. to verb3k and FakeOutdoorsman for their great work on the How To's

So here is my very short version to get you running. Some is directly quoted so like I said all props. to the How To creators.

Step 1
This option is only available for Ubuntu Karmic Koala 9.10. To install FFmpeg from Medibuntu open Terminal (Applications -> Accessories -> Terminal) and run the following:

```
sudo wget http://www.medibuntu.org/sources.list.d/`lsb_release -cs`.list --output-document=/etc/apt/sources.list.d/medibuntu.list && sudo apt-get -q update && sudo apt-get --yes -q --allow-unauthenticated install medibuntu-keyring && sudo apt-get -q update
```

then (here I'm adding nautilus-open-terminal) the reason will be clear later for open terminal. MPlayer will be fine for the player so I wont add VLC.

```
sudo apt-get install ffmpeg libavcodec-extra-52 nautilus-open-terminal
```

Step 2
Capturing the screen

```
ffmpeg -f alsa -i pulse -f x11grab -r 30 -s 1366x768 -i :0.0 -acodec pcm_s16le -vcodec libx264 -vpre lossless_ultrafast -threads 0 output.mkv
```
My Screen is 1366x728 so you will want to at least change that part if nothing else.

Then press enter to start the capturing process. To stop recording, go back to the terminal and press q.

In the above command, we capture audio from pulse (pulseaudio sound server) and encode it to lossless raw PCM. Then, we grab a video stream from x11 at a frame rate of 30 and a size of 1366×768 from the display :0.0 and encode it to lossless h264 using libx264. Using -threads 0 means automatic thread detection. If your distribution does not use the pulseaudio sound system, replace &#8220;-i pulse&#8221; with &#8220;-i /dev/dsp&#8221;. The resulting streams will be muxed in a Matroska container (.mkv). The output file &#8220;output.mkv&#8221; will be saved to the current working directory.

Now see the last part where "The output file &#8220;output.mkv&#8221; will be saved to the current working directory." This is why we want nautilus-open-terminal.
This way you can browse to where you want it saved, right click and select "Open in Terminal" before running the capture command.
The captured video is big (close to 70 MB for a 4 minute video).
So if you have a partition with a lot of space you can have it save it there automatically this way, otherwise it would be saved to your Home Folder by default.
Unless of course you either edited the command to save it elsewhere or used cd to get to that folder first.

An added benefit is that it could be re-encoded to a variety of formats like avi to be played without the disc as explained in the How To in Step 2.

I would try it for a couple minutes then stop it and check to see if it was successful or not. Remember how.
Then **press enter to start the capturing process**. **To stop recording, go back to the terminal and press q**.

Hope you get your pics. it sounds like a common scam they pull.

---

### Post by nothingspecial on 2010-03-30
> **Eathray said:**
> nothingspecial,

Thanks man. I appreciate every thought... except maybe the guy who thinks I murdered my gardener... still don't quite get that reply...  :)

Probably doesn`t shave yet and has no idea.

He`ll be embarased about that post for years. :p

---

### Post by Eathray on 2010-03-30
2hot6ft2,

Wow, that's a wealth of input. Thanks for the time that must have taken.

Yes, we are now aware from others how photo-scams work after our experience, and apparently this is very common, especially the part about holding the pics hostage for more money, trying to bump people into a higher package when you've already paid for the package you bought. Unbelievable.

I'm going to read it all through very carefully, and thanks again.

Eathray

---

### Post by Eathray on 2010-03-30
nothingspecial,

Haha. I guess dragging a razor down your throat is a test of your maturity isn't it... knowing when not to get overly excited. :P

Eathray

---

### Post by 2hot6ft2 on 2010-03-30
You're welcome, and I'm sure you'll get your pics. it's just a matter of how and when.

---

