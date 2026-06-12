---
title: "Image viewer maxing out CPU"
date: 2014-03-31
forum: Multimedia Software
---

### Post by rlaracuenti on 2014-03-31
Trying to get to the root of this problem. Not sure why it is happening. I am using the command:

# eog -s path/to/file 

to loop any images in that particular folder. The image files are rather large but still something doesn't seem right.

Even after I have closed the image the processes still show multiple instances of eog and the cpu is still maxed out.

This computer needs to run essentially 24/7 so I don't want it to burn out.

Any ideas?

---

### Post by sudodus on 2014-03-31
Welcome to the Ubuntu Forums :-)

It works for me without problems. Maybe you have too weak CPU or too little RAM. I think the viewer ***feh*** is lighter. You can install it from the repositories from the Software Center or via the command line

```
sudo apt-get install feh
```

See ```
man feh
``` to find the correct options. If still problems, please post the specs of your computer

- Brand name and model
- CPU
- RAM (size)
- graphics chip/card

- what version of Ubuntu you are running
- and finally how big are the pictures (width x height) in pixels

---

### Post by rlaracuenti on 2014-03-31
Thanks for the reply. It isn't a particularly beefy computer. It's got 1.8 ghz dual core, 4 GBs Ram, Intel gma 3650 integrated graphics running ubuntu 12.04. I was thinking there had to be something wrong with the command because even after I close the program I still have 4 or 5 instances of eog running. That's what got me curious as to what's going on.

I will give feh a try tomorrow. Does it accept command line arguments so I can set it to loop photos automatically at boot?

---

### Post by tgalati4 on 2014-03-31
It might be a bug in eog.  I believe it opens a new thread for each image.  On loop mode, that would be a problem.  To work around it, you could write a script to run eog on loop mode for so many minutes then *killall eog* and loop that inside the script.  If you have an Intel graphics card that shares video RAM with regular RAM, then your CPU would up because of all the extra RAM handling.  If your motherboard has a crappy southbridge (the memory IO support chip) then that would contribute to the slowness.

---

### Post by sudodus on 2014-04-01
> **rlaracuenti said:**
> Thanks for the reply. It isn't a particularly beefy computer. It's got 1.8 ghz dual core, 4 GBs Ram, Intel gma 3650 integrated graphics running ubuntu 12.04. I was thinking there had to be something wrong with the command because even after I close the program I still have 4 or 5 instances of eog running. That's what got me curious as to what's going on.

I will give feh a try tomorrow. Does it accept command line arguments so I can set it to loop photos automatically at boot?

Yes, feh is made to work with command line arguments. I use the following ***alias*** for a slide-show. (Feh uses files in a whole directory tree, which is better than eog).

```
alias fehs='feh -r -F -V -d -Z -z -D 5'
```

Let us say you have a directory tree Pictures in your home folder. After creating the alias, run these commands

```
cd ~/Pictures
fehs

```

Are you familiar with aliases? If not, let me know, and I can explain more.

---

### Post by rlaracuenti on 2014-04-01
Awesome, thanks for the all the info. I have not used alias's before but I see how that's incredibly useful. I'm going to try "feh -r -F -V -Z -Y -D 10 path/to/file" since I don't want it randomized and -Y to hide the pointer. So, for alias a quick search brought me here

[http://www.howtogeek.com/73768/how-to-use-aliases-to-customize-ubuntu-commands/](http://www.howtogeek.com/73768/how-to-use-aliases-to-customize-ubuntu-commands/)

So, all I have to do is create the file and that's it? It doesn't have to be put anywhere special or activate in any way? Also, it looks like I can have as many alias' as I want in one file? Is that the case... Sounds great, probably don't need it in this case since the computer pretty much runs unattended but definitely useful for my own everyday computing (same - 12.04). 

tgalati - that does sound correct. It didn't make sense to me to have so many instances of eog running - each one of them hogging up a ton of cpu and memory on their own. And I had an awful time getting ubuntu to run on these machines (cedarview display drivers - what a nightmare!) and its integrated video so it may very well be the case that ram is shared.

Hopefully feh will solve this problem - I'll take a look at the processes later since the pictures are displayed publicly - actually I can just ssh and top.

Thanks again. I'm working on a script that will autoplay anything you put in certain folders, I'm half way there but I'll definitely post a a new thread for that.

---

### Post by sudodus on 2014-04-01
I put my aliases into the file **~/.bashrc** ('bash running conditions', which sets the conditions for each instance of bash, for example in terminal windows). There are already some aliases there, for example

```
alias ll='ls -l'
```

and I put my own aliases in a group together with the original aliases.

It is also possible to create a separate file for the aliases, for example **~/.aliases **and call that file from **~/.bashrc**

After saving the file (when you added a line with your alias), it will be active in the next terminal window that you start.

[COLOR=#696969]If you want to make it active in a window that is already opened you can run the command

```
source ~/.bashrc
```
[/COLOR]

---

### Post by rlaracuenti on 2014-04-01
Thanks for the help. Feh seems to be doing much better. It's still opening up multiple instances that persist after I've closed the program but they are nearly as cpu intensive. I'll look into the suggestion of somehow killing the extra processes on a regular interval. Thanks again.

---

### Post by sudodus on 2014-04-01
You are welcome and good luck :-)

---

