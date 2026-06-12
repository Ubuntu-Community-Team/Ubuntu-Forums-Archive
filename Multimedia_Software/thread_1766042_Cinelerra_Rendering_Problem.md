---
title: "Cinelerra Rendering Problem"
date: 2011-05-23
forum: Multimedia Software
---

### Post by importsjc on 2011-05-23
Hi, i started using cinelerra and liked the features but when i tried to render the video i was editing, it came out with weird colors! Like red is blue and vice-versa! it worked fine previewing it before i rendered it but it messed up afterwards. it might be my fault but i tried another video and the same thing happened. I would love help because i really liked it! also tell me if you need more info. thanks.

---

### Post by no2498 on 2011-05-24
this may help you

[http://www.g-raffa.eu/Cinelerra/HOWTO/index.html](http://www.g-raffa.eu/Cinelerra/HOWTO/index.html)

---

### Post by importsjc on 2011-05-24
i have looked at this page before.....what am i looking for? i don't see the answer in there.

---

### Post by StrayEddy on 2011-05-24
Did you set an effect in your video?

Is your video an mpeg file? (it pops errors for me if i use another video format)

In what format did you render it?

Give us more info about the type of rendering your trying to do.

---

### Post by importsjc on 2011-05-24
here is what it looks like when it renders

---

### Post by StrayEddy on 2011-05-24
Did you install the CV (Community Version) of Cinelerra. It's the best one, most up-to-date:

[http://cinelerra.org/](http://cinelerra.org/)

---

### Post by importsjc on 2011-05-24
it was an avi and i rendered into "quicktime for linux" and no effects were added.

---

### Post by StrayEddy on 2011-05-24
Try running cinelerra in the terminal instead. Maybe you ll see an error in the terminal while rendering.

---

### Post by importsjc on 2011-05-24
the file was an avi and i rendered it to a "Quicktime for linux" format. i downloaded the source code for cinelerra from here [http://heroinewarrior.com/cinelerra.php#download](http://heroinewarrior.com/cinelerra.php#download). i don't know if that is the community version or not! but ill try useing cv.

---

### Post by StrayEddy on 2011-05-24
No that is not the Cinelerra-CV.

Yes, you should get it first before trying to solve your problem.

---

### Post by importsjc on 2011-05-24
i tried the link you gave me and went to the download page. but the only thing that gave me for ubuntu was this site! 

[https://launchpad.net/~cinelerra-ppa](https://launchpad.net/~cinelerra-ppa)

maybe i missed something but i don't see it....

---

### Post by StrayEddy on 2011-05-24
Here is what you need to do:

1- remove cinelerra completely from your desktop: (ex: sudo apt-get remove cinelerra)

2- open a terminal

3- sudo add-apt-repository [B]ppa:cinelerra-ppa/ppa

[/B]4- sudo apt-get update

5- sudo apt-get install cinelerra


That should work.

FYI: a ppa is a link to where the package to install is, it's an easy way to get the latest version of a software.

PS: THIS ONLY WORKS IF YOU HAVE **UBUNTU 9.10 OR LATER**

---

### Post by StrayEddy on 2011-05-24
Do you have ubuntu 9.10 or later ?

If not, tell me cause there is another way to install it.

---

### Post by importsjc on 2011-05-24
i have ubuntu 10.10. hmmmm after installing cinelerra cv it still rendered the same way! maybe its a setting. or some thing is wrong with my computer!

---

### Post by StrayEddy on 2011-05-24
Did you install your video card drivers, maybe that s where your problem is?

---

### Post by importsjc on 2011-05-24
how would i check that in ubuntu? sorry im not that familar with ubuntu yet....im working on it.:)

---

### Post by importsjc on 2011-05-24
i just installed cinelerra cv on my virtual ubuntu computer and it rendered the same way! the machine is default ubuntu so its not a setting. :o

---

### Post by StrayEddy on 2011-05-24
Ho k, virtual computer, like VMWare...VirtualBox...or Wubi maybe ?

I think THAT is the problem, you can get weird stuff in Virtual desktops, it s best to have ubuntu installed for this kind of work.

If you have Windows and you don't want to switch to Ubuntu you don't have to.

You can just dual-boot:

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by importsjc on 2011-05-24
i must have said that wrong....i have ubuntu installed as a dual boot and i tried cinelerra in ubuntu. but when cinelerra didn't work in the dual boot i tried it in a virtual machine to see if it would change what happens.

---

### Post by StrayEddy on 2011-05-24
For your video card, first open a terminal and type:

lspci | nvidia

If nothing shows type:

lspci | ati

If still nothing type:

lspci

And search for your video card.

When you know your video card model go to the website of the company (ATI, Nvidia...) and download the drivers from there.


PS: Yeah sorry for last post, i understood that after i posted it hehe, my bad.

---

### Post by importsjc on 2011-05-24
ok i downloaded the driver. now how do i install it? my card was an ATI Radeon HD 4200

---

### Post by StrayEddy on 2011-05-24
I think you downloaded a .run file, so here is what you do:

[https://help.ubuntu.com/community/InstallingRunPackage](https://help.ubuntu.com/community/InstallingRunPackage)

---

### Post by importsjc on 2011-05-24
hmmm....still not working! this is the driver i downloaded and installed.

[http://support.amd.com/us/gpudownload/linux/10-4/Pages/radeon_linux.aspx?type=2.4.1&product=&lang=us&rev=10.4&ostype=Linux%20x86_64](http://support.amd.com/us/gpudownload/linux/10-4/Pages/radeon_linux.aspx?type=2.4.1&product=&lang=us&rev=10.4&ostype=Linux%20x86_64)

---

### Post by StrayEddy on 2011-05-24
K, now maybe you should try what i said before.

Run cinelerra in the terminal.

Then do the rendering and checl in the terminal for any errors.

To open the terminal: Ctrl+Alt+T

---

### Post by importsjc on 2011-05-24
there were no error messages just:

Render::run 1
Render::run 2
Render::run 3

all the way to:

Render::run 10

---

### Post by StrayEddy on 2011-05-24
Could you take screenshots of your cinelerra settings, so i could check it.

Really that s shame it doesn t work for you. There is no real replacement for cinelerra in linux, it s the best for us.

---

### Post by importsjc on 2011-05-24
ok when i click preferences under settings(i think thats what you mean by "cinelerra settings")it just exits out of cinelerra!

this is getting annoying! :)

P.S. Thanks so much for spending the time to help! i really appreciate it!

---

### Post by StrayEddy on 2011-05-24
Yes, that s where the settings are.

I should have asked before but in what purpose will you use cinelerra, maybe you don't need it, kdenlive and openshot can do a great job too.

So what are you trying to do with it?

---

### Post by importsjc on 2011-05-24
well i liked the chroma key function (green screen) and the audio and video effects will really come in handy. i am trying to be able to 

1 use green screen
2 edit audio
3 normal editing and some advanced editing for videos

i could find any thing else that was free that would let me do that!

---

### Post by importsjc on 2011-05-24
so what ive gathered from what you said is "maybe its my computer and if i download cinelerra on a different computer it will work better?"

i just want to know if this isn't cinelerra's fault.

---

### Post by StrayEddy on 2011-05-24
Openshot and kdenlive can let you do all that.

I Used Kdenlive 1 year ago maybe, really good but sometimes go corrupted.

Openshot is younger than openshot but has a lot of functionnality.

Install each of them and try them out, all the functionnalities you need are there.

Openshot and kdenlive are really easier to install and normally work out-of-the-box.


Good luck, hope you ll like it.

---

### Post by StrayEddy on 2011-05-24
> **importsjc said:**
> so what ive gathered from what you said is "maybe its my computer and if i download cinelerra on a different computer it will work better?"

i just want to know if this isn't cinelerra's fault.


Well it works on mine hehe. And is really really great, as powerfull as adobe premiere pro i would say, but with less effects.

Cinelerra is not really stable, so i wouldn t say it s your computer fault. It s maybe cinelerra fault for not functionning on your desktop.

---

### Post by importsjc on 2011-05-24
ok thanks! ill try them.

---

