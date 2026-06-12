---
title: "Can't install Skype"
date: 2009-06-30
forum: Multimedia Software
---

### Post by Mikethebook on 2009-06-30
I tried to download Skype from the Skype website, the Ubuntu version but when I came to run it, I had the error message: Dependency is not satisfiable: libqt4-core (>=4.2.1). Detailed easy to understand explanations please as I am a total novice. Everything is new.

---

### Post by Bucky Ball on 2009-06-30
Install the Medibuntu repository to your software sources and you will find the latest Skype in Synaptic Package Manager afterwards:

[https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

Open a terminal (Applications->Accessories) and copy and paste the correct code for your version of Ubuntu.

---

### Post by Vaidok on 2009-06-30
If you don't want to add the repo. You can just open up the terminal and type "sudo apt-get install libqt4-core" without the quotes.

---

### Post by Mikethebook on 2009-06-30
Thanks for the information guys but I'm still in the dark. Can you claify further. Repositories!!! I'm a first time user from a Windows background.

---

### Post by Bucky Ball on 2009-06-30
Try what Vaidok mentions first. Open a terminal (Applications->Accessories->Terminal) copy and paste (control/shift/v to paste in a terminal):

```
sudo apt-get install libqt4-core
```Try again. If that doesn't work, open a terminal and from this page:

[https://help.ubuntu.com/community/Me...20Repositories]("https://help.ubuntu.com/community/Medibuntu#Adding%20the%20Repositories")

... copy and paste the appropriate command for your version of Ubuntu, for instance, for Hardy 8.04 you would use this one:

```
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) --output-document=/etc/apt/sources.list.d/medibuntu.list

```then the key:

```
sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update
```Don't forget the key, very important.

Then go to:

System->Administration->Synaptic Package Manager

... and search for Skype. Install and you should be good to go. :)

Let us know if you are having problems.

---

### Post by Mikethebook on 2009-06-30
Thanks. I got as far as the Synaptic Package Manager and then got lost. Scrolling down i found several files called Skye something or other but couldn't manage to get them all ticked. There was one called simply Skype seemed to also require Skype Common. I really didn't know how to mark the right ones and then how to download them.

---

### Post by Revolutionary101 on 2009-06-30
You could also open terminal and type

```
sudo apt-get install skype
```

---

### Post by Mikethebook on 2009-06-30
Thanks And that would do everything else would it?

---

### Post by dtoronto on 2009-06-30
Here's the community documentation for Skype.  I think you need the medibuntu or skype database added to your repository.

[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by lindsay7 on 2009-06-30
I had a similar problem. Try uninstalling skype programs form Synaptic. There may be two marked. Then install again form their web site.

---

### Post by Revolutionary101 on 2009-06-30
> **Mikethebook said:**
> Thanks And that would do everything else would it?

Yeah that would download all of the packages needed for Skype to work.

---

### Post by Bucky Ball on 2009-07-01
Don't scroll looking for it; use the 'Search' function in Synaptics. You got that far so you are doing well.

Yes, 

sudo apt-get install skype

in a terminal should do the same thing, but only if you have the medibuntu repository which it sounds like you have (if you are finding Skype in synaptics).

---

### Post by Mikethebook on 2009-07-01
Yhanks for holding my hand through this. Can you talk me through the search and installation . . . both ways.

---

### Post by Mikethebook on 2009-07-01
Thanks for all the help. Skype opens up nicely. Next on my list will be trying to get the computer's integral webcam and microphone to work. Any thoughts!! One the face of it, Ubuntu seems simple to use and wonderfully stable and I'll be happy if I can get it to work for my wife who needs computer simplicity rather than Vista!! But I'm finding it incredibly complex beneath the surface and still have a list of applications to sort out as well as the wireless!

---

### Post by Mikethebook on 2009-07-01
One more problem with Skype. I opened it up and it came up with the error message: another Skype instance may exist. What do I do?

---

### Post by Bucky Ball on 2009-07-01
Have you got skype open already? Have you still got the one you installed earlier still installed?

Just remember Linux is not Windows and vice versa and you'll be fine; just enjoy the learning curve and a different way of computing!

I would suggest for your other questions, you post again, giving as much information as you can about your computer (brand, model) and the problems you are having. Please include your version of Ubuntu, there are many flavours and subtle differences. It will help if you can post as much about your hardware as possible also. 

Reasoning for posting again: Threads get lost in the busy traffic and the heading of this one concerns Skype so people that may be able to help with wireless will not look for it. Post the address of your new thread(s) here and I will join in if I can help.

Wireless: can you plug an ethernet cable into your computer to start and get your updates. This will sometimes load the appropriate drivers for you. The reason some hardware (wireless, graphics cards) do not work 'out of the box' is the drivers are third party and therefore not included with Ubuntu install (you have to personally enter into an agreement with the owner of the licence for the software).

The update should pick up your restricted driver requirements and act accordingly with a series of question and answer windows and then you will hopefully be good to go (with some tweaking to do!). Once you get there, the stability is worth the effort. 

Mic: Double click the speaker icon and have a look in there to make sure nothing is muted (red cross at the bottom of the slider), esp. 'ext mic'.

Skype: Open a terminal and type or paste 'killall skype', without the apostrophes, then open Skype as normal.

Good luck.

---

### Post by Pepe Lebuntu on 2009-07-17
Hey there,

I've just installed Skype onto my system, and it doesn't seem to be working. It's on my applications/network folder fine, but when I go to load it from there, I get an error message:

Binary File corrupt. Please reinstall Skype.

I have since reinstalled Skype - originally, I'd installed it from their website, and for the reinstall I just used the Terminal... I'm having trouble seeing it on Synaptic, even though I've installed the medi-thingy through Terminal.

Any thoughts? Much appreciated.

---

### Post by Bucky Ball on 2009-07-17
If you have added the Medibuntu repository to your software sources correctly, you will find Skype by using the search function in Synaptics.

If you search for Skype and it is not there (in Synaptics), then you have not added the Medibuntu repo correctly and should maybe trace your steps there.

Go to System->Administration->Software Sources->Third party and just make sure the Medibuntu repository is there. If not, go again. :)

---

### Post by Pepe Lebuntu on 2009-07-18
Cool thanks for that. I checked the Software Sources, and it was there, but for some reason hadn't been "ticked". I've since done that, but it's still coming up with the same problem - not in Synaptics. Until I install it through Synaptic, I won't be able to get an un-stuffed Skype, right?

Thanks Bucks.

---

### Post by Bucky Ball on 2009-07-18
Use update manager at System->Administration or in a terminal:

```
sudo apt-get update
```

Then search again.

---

### Post by Pepe Lebuntu on 2009-07-18
she-BANG! Done! Thanks heaps mate. Just goes to show you DO get more bang for your Buck when you're on the Ball. ;)

---

### Post by Bucky Ball on 2009-07-18
Good news, pleased to hear it and welcome to Ubuntu and the forums.

And Hello from ... Adelaide! I live there too! Good to see other Adelaide users here. \\:D/

---

### Post by Pepe Lebuntu on 2009-07-18
Small world in linux! :)

---

