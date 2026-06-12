---
title: "mp3 splitter installation 16.04"
date: 2016-04-25
forum: Multimedia Software
---

### Post by newblank25 on 2016-04-25
i downloaded mp3split-gtk.09.tar.gz. i opened the install file& followed the directions for input to terminal but got error message that file wasn't there. Thx for help

---

### Post by squirrel3 on 2016-04-26
Try this installation method, via software center. 

[https://apps.ubuntu.com/cat/applications/mp3splt-gtk/](https://apps.ubuntu.com/cat/applications/mp3splt-gtk/)

---

### Post by howefield on 2016-04-26
> **newblank25 said:**
> i downloaded mp3split-gtk.09.tar.gz. i opened the install file& followed the directions for input to terminal but got error message that file wasn't there. Thx for help

Please copy and paste the terminal output (the command entered and the output of it) back here so that we can see the errors verbatim, and please use code tags :)

---

### Post by newblank25 on 2016-04-26
these are the instructions. this is what i got when i did that.
```
michael@michael-p7-1456c:~$ sudo dpkg -i libmp3splt.deb
[sudo] password for michael: 
dpkg: error processing archive libmp3splt.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 libmp3splt.deb
michael@michael-p7-1456c:~$ sudo  dpkg -i mp3splt-gtk.deb
dpkg: error processing archive mp3splt-gtk.deb (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 mp3splt-gtk.deb
```
thx for help

---

### Post by howefield on 2016-04-26
The instructions tell you download the libmp3splt.deb and then install it.

Sounds like the error has told you what is wrong, "*No such file or directory*" - in other words no such file or directory :)

Incidentally I am not sure that you will get this working on 16.04.

---

### Post by newblank25 on 2016-04-26
thx for information. It was a good and easy  program to use in ubuntu 14.04 but I'm good using audacity.

---

### Post by howefield on 2016-04-27
> **newblank25 said:**
> thx for information. It was a good and easy  program to use in ubuntu 14.04 but I'm good using audacity.

Cool, Audacity would have been my recommendation.

---

### Post by jnquick on 2016-05-26
I miss mp3splt since changing from 15.04 to 16.04. Ubuntu doesn't even seem to find it,  Synaptic package manager says that it is there. Any help getting it to function in 16.04 would  be appreciated.
I have and have used audacity but mp3splt is very efficient for my purposes which is splitting 10 to 20 hour mp3 files into 1 hour equal segments. I will try to load the file in audacity and see if it will even load much less handle it.

---

### Post by howefield on 2016-05-26
> **jnquick said:**
> I miss mp3splt since changing from 15.04 to 16.04. Ubuntu doesn't even seem to find it,  Synaptic package manager says that it is there. Any help getting it to function in 16.04 would  be appreciated....

What's the problem, have you installed it or are you getting some sort of error ?

---

### Post by mc4man on 2016-05-26
Debian removed the gtk package so it's not available in 16.04
[https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=803000](https://bugs.debian.org/cgi-bin/bugreport.cgi?bug=803000)

You can probably download [the 15.10 package]("https://launchpad.net/ubuntu/+source/mp3splt-gtk") & then install using apt, ie., ex. dl'ed to ~/Downloads

sudo apt install ~/Downloads/mp3splt-gtk_0.7.2-2ubuntu3_amd64.deb

---

### Post by jnquick on 2016-05-26
"What's the problem, have you installed it or are you getting some sort of error ?"
It is installed, but Ubuntu's application launcher doesn't find it.

I just finished using Audacity and it will work, but for my purposes which is breaking the file into equal length small files, I have to id where the break occurs and then label each subfile.

"You can probably download the 15.10 package & then install using apt, ie., ex. dl'ed to ~/Downloads

sudo apt install ~/Downloads/mp3splt-gtk_0.7.2-2ubuntu3_amd64.deb"

Thanks, I will try this.

jnq

---

### Post by jnquick on 2016-05-26
I used Audacity and it will work but is repetitive and cumbersome. For my purposes mp3splt was much better. 

I tried to just 
sudo apt install ~/Downloads/mp3splt-gtk_0.7.2-2ubuntu3_amd64.deb
and got an unsupported file message.

---

### Post by mc4man on 2016-05-26
> **jnquick said:**
>  

I tried to just 
sudo apt install ~/Downloads/mp3splt-gtk_0.7.2-2ubuntu3_amd64.deb
and got an unsupported file message.
If you're on a 32bit install then you use the i386 package

---

### Post by shantiq on 2016-05-30
excellent!

even lazier route one command :]

for 64 >>

```
cd Downloads ; wget https://launchpad.net/ubuntu/+archive/primary/+files/mp3splt-gtk_0.7.2-2ubuntu3_amd64.deb &&  sudo apt install ~/Downloads/mp3splt-gtk_0.7.2-2ubuntu3_amd64.deb
```

for 32 >>

```
cd Downloads ; wget https://launchpad.net/ubuntu/+archive/primary/+files/mp3splt-gtk_0.7.2-2ubuntu3_i386.deb \
&&  sudo apt install ~/Downloads/mp3splt-gtk_0.7.2-2ubuntu3_i386.deb 

```

---

