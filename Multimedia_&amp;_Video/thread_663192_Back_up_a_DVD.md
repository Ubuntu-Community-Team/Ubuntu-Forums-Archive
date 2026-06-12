---
title: "Back up a DVD"
date: 2008-01-09
forum: Multimedia &amp; Video
---

### Post by fourthdimension on 2008-01-09
Hey All

I have a DVD I'm trying to back up before I let a friend borrow it.  I've tried using k9 copy to rip it, but it keeps generating an unspecified error (same with DVD rip), and I've tried just plain copying it, but it plays all scrambled after the burn.  I've read some other topics on this subject, but they all deal with compressing the textures and changing the formats, and since this DVD has a lot of special effects, I really don't want to lose any quality...  does anyone know how to back it up?
Thanks.

---

### Post by mouseboyx on 2008-01-09
Try using dvd95 ```
sudo apt-get install dvd95
```

---

### Post by fourthdimension on 2008-01-09
Thanks.  That doesn't seem to work either, though...  it gives me another unspecified build error and conversion error.
Would that have something to do with the trace level?  I don't know what to set that to...

---

### Post by Patterson on 2008-01-09
You may also try to copy to dvd software.

---

### Post by fourthdimension on 2008-01-09
?

---

### Post by alecz20 on 2008-03-22
My first try was with DVD95. 

I opened it, and I selected the audio and subtitles, then i clicked "Evaluer" and it left the compute quality at 100%. Anyway, I clicked "Convert" and it did its thing, then I was prompted to Play, or Forward. I clicked Play... nothing happend, I clicked Forward nothing happened either.

Then I decide to look into the preferences and I noticed that the temporary folder and the iso folder was the same, I tried to close and it prompted me that they should be different (then why was it like that by default????)

In any case... I put a different one. Then i noticed that the player was Xine, which i don't have, so I switched to vlc. Then I wanted to check the output. There was no ISO image... so I wasn't sure that the whole DVD had been copied.

I decided to give one more try... with the new settings (other ISO folder, and VLC instead of Xine), and guess what: "Conversion error......." that's it!

So it worked only once.... then it died... I have no idea what went wrong.

Second, I gave K9Copy a try.... (remember that I'm running GNOME), and guess what, a dozen errors from "Communication Error, check that dcopserver is running", and then.... permission errors in /home/alex/.kde/share/configuration.... I checked the folder, and it's owned by root, so... what's going on?

then... MIME errors, "no MIME types installed".....

Basically, K9Copy CANNOT work under GNOME!!!!

Now I'm afraid I'll have to go back to DVD Shrink for Windows using WINE...

I'll come back and let you know how it went :S

Its sad that both DVD95 and K9Copy failed (i.e. did not work out of the box) :(

---

### Post by mc4man on 2008-03-22
> Basically, K9Copy CANNOT work under GNOME!!!!
actually k9 works just fine in gnome (except for some structure protections it can't handle )
> permission errors in /home/alex/.kde/share/configuration.... I checked the folder, and it's owned by root,
you should look at how you installed k9 - you certainly should have permissions there

---

### Post by alecz20 on 2008-03-22
I installed k9 with the Add/Remove... feature in ubuntu. Is there a better way?

Thanks!

---

### Post by SirThom on 2008-03-22
I am also an ubuntu n00b and had the exact same problem that you did.  As you may be aware, Ubuntu doesn't come with the codices needed to watch DVDs.  There is a whole back story in that about how they were supposedly secret, and then somebody reverse engineered DVDs to find them and they were published in 2600 magazine, etc. etc.
Well, I thought that I had installed toe proper codices, but I hadn't.
I'm trying to find the instructions that finally worked for me.  I think it may have been these
[http://www.cyberciti.biz/faq/howto-ubuntu-linux-playback-dvd/](http://www.cyberciti.biz/faq/howto-ubuntu-linux-playback-dvd/)

Prior to installing the codices, I could only view or copy DVDs that I had previously *ahem* backed up myself (non-copy protected).  Now they all seem to work.

---

### Post by alecz20 on 2008-03-22
I have no problems watching the DVD's with VLC....

Not sure about the codecs and stuff, but I guess if VLC can play them.... I have them, right? (or not?)

---

### Post by alecz20 on 2008-03-22
I checked the guide you posted the link to... I already have libdvdread3 installed, so that's not my problem :S

---

### Post by mc4man on 2008-03-22
Check the permissions  of the .kde folder itself in home

---

### Post by alecz20 on 2008-03-22
> **mc4man said:**
> Check the permissions  of the .kde folder itself in home

The .kde folder is owned by me, but everything inside it is owned by root.

---

### Post by alecz20 on 2008-03-22
And another thing... I downloaded DVD95 from sourceforge, compiled it and installed it. The process was in the regular steps of
- ./configure
- make
- make install

However it did not help (it was a newer version though)
Now I want to remove this program, how do I do that?:confused:


Ohh, and DVD shrink runs in WINE but it cannot compress more than 65% so it can't make it small enough for a 4.7GB disc.... this is ridiculous, I'm gonna give it a try in windows also to see if it's a limitation on DVD Shrink or WINE.

---

### Post by SirThom on 2008-03-22
> **alecz20 said:**
> I checked the guide you posted the link to... I already have libdvdread3 installed, so that's not my problem :S

OK.  I thought that I had mine installed too, via synaptic package manager or summat, but sending those commands through again worked so it's worth a shot, right?

---

### Post by mc4man on 2008-03-22
> Now I want to remove this program, how do I do that
in most cases cd to your build directory and run sudo make uninstall

---

### Post by alecz20 on 2008-03-22
> **SirThom said:**
> OK.  I thought that I had mine installed too, via synaptic package manager or summat, but sending those commands through again worked so it's worth a shot, right?

Yep... it's no harm in trying again, however it did not chance anything to my system. Note that I did 'sudo aptitude install libdvdread3' and 'sudo apt-get install libdvdread3', however nothing was changed (updated) to my system.

---

### Post by mc4man on 2008-03-22
as far as your other issue i'm just learning myself but what I'd try is first go to properties of .kde and under permissions click  apply permissions to enclosed files. If that didn't work I'd try 
```
sudo chown -R username:username ~/.kde
```   -with your user name

---

### Post by alecz20 on 2008-03-22
> **mc4man said:**
> as far as your other issue i'm just learning myself but what I'd try is first go to properties of .kde and under permissions click  apply permissions to enclosed files. If that didn't work I'd try 
```
sudo chown -R username:username ~/.kde
```   -with your user name


I was thinking about the same thing, but I was just worried, why would Ubuntu set the permissions like this? Maybe there is a good (security) reason for it...?

---

### Post by alecz20 on 2008-03-23
Hmm, I just ran k9copy from terminal to see more details about the errors, and I noticed that each error message was accompanied by several "Permission Denied" messages, so I decided to take the plunge and open a gaping security hole :lolflag:

And.... it worked!!! The only message I get now is 

'k9copy: ERROR: : couldn't create slave : Cannot talk to klauncher'


but the copying is running, so.... I hope it's gonna be alright.

Still, how about DVD95 ??? why do I get "conversion error' and how do I remove it if I installed it using ./configure -> make -> make install  ?

---

### Post by mc4man on 2008-03-23
How you got to where you are i don't know but you should own everything in .kde - folders, files, links

---

### Post by alecz20 on 2008-03-23
Well, I do own them all now... Thanks for the help, now I'm compressing the DVD, I'll post my results when it's done.

Also... I never touched the .kde folder before. I was just avoiding kde apps, especially because of the 'dcopserver error' which I have no idea what it means, but starting if from the terminal makes the error go away.


P.S. I had to use the terminal to change the persmissions:
' sudo chown -R alex:alex ~/.kde '

and how about the klauncher error?

---

### Post by alecz20 on 2008-03-23
> **alecz20 said:**
> And another thing... I downloaded DVD95 from sourceforge, compiled it and installed it. The process was in the regular steps of
- ./configure
- make
- make install

However it did not help (it was a newer version though)
Now I want to remove this program, how do I do that?:confused:

...


For anyone that wants to know how to remove stuff installed using the above steps check this threads:

[http://www.linuxforums.org/forum/slackware-linux-help/41691-uninstall-applications.html](http://www.linuxforums.org/forum/slackware-linux-help/41691-uninstall-applications.html)

and

[http://ubuntuforums.org/archive/index.php/t-2356.html](http://ubuntuforums.org/archive/index.php/t-2356.html)

Basically the idea is to use a program called 'checkinstall' and run it as root right after 'make install' this will create a .deb package.

You can use this package to install it on other machines.

After the package is created you can easily remove the program using the command:
'sudo dpkg -r  programname'

in my case: 'sudo dpkg -r dvd95' and it was gone.

While there still is some debate over how clean packages work, this was fine for me :D

---

### Post by stinger30au on 2008-03-23
piece of cake.
install wine from repo's.
install K3B burning s/w from repos

install dvdfab free
[http://www.dvdfab.com/free.htm](http://www.dvdfab.com/free.htm)

let it copy the move to *HARD DRIVE*
the burn the data back to dvd with k3b, works a charm.
i have to burn back with k3b or it will fail :-(

---

### Post by alecz20 on 2008-03-23
I checked the website for dvdfab. Sounds like an interesting application (for Windows).

However, k9copy seems to work, it creates the ISO now. I will try dvdfab next time I'll be stuck with copying a DVD (oh, and they say DVDfab also works with HD-DVD and Blu-Ray)

I have a question though.... is this program free or just trial?

---

### Post by alecz20 on 2008-03-23
I successfully created a ISO image using k9copy. I mounted it with Gmount-iso and i opened the mounted folder with VLC, and everything worked fine. Now I am burning it with the Ubuntu CD/DVD creator (via Right-click on the image, and burn baby, burn!)

Still poor DVD95 failed to do its job, and we could not find any solution to it. K9copy worked fine after a bit of "tunning"

I wanted to use K3B to create the DVD but I was getting the "klauncer error" anyone knows what that is?


Well, as far as I'm concerned this thread can be marked as [SOLVED]

and again congratulations to the Ubuntu Team, the Ubuntu Community and the Linux community as well.

---

