---
title: "Slimjet browser availability in Ubuntu Software Centre"
date: 2016-02-17
forum: Multimedia Software
---

### Post by mark253 on 2016-02-17
Hi, 
on the page below
[https://apps.ubuntu.com/cat/applications/slimjet/](https://apps.ubuntu.com/cat/applications/slimjet/)
it is stated that Slimjet browser in in Ubuntu Software Center. 
Unfortunately when I start USC in my computer a can't find Slimjet.
Why ?

---

### Post by QIII on 2016-02-17
Hello!

Which release of Ubuntu are you using?

---

### Post by shantiq on 2016-02-17
hmmm slimjet new one on me :]
do not know the answer to the Ubuntu Software Center but it installs well on 14.04 with

```
 sudo apt-get install libappindicator1
```
and  ```
sudo apt-get -f install
```       first as missing
then using [http://www.slimjet.com/en/dlpage.php](http://www.slimjet.com/en/dlpage.php) deb here

```
 sudo dpkg -i slimjet_amd64.deb
```


but maybe you have already nstalled it and are only wanting to know about the Ubuntu Software Center issue

---

### Post by mark253 on 2016-02-17
I am using Xubuntu 14.04.

---

### Post by mc4man on 2016-02-17
> **mark253 said:**
> Hi, 
on the page below
[https://apps.ubuntu.com/cat/applications/slimjet/](https://apps.ubuntu.com/cat/applications/slimjet/)
it is stated that Slimjet browser in in Ubuntu Software Center. 
Unfortunately when I start USC in my computer a can't find Slimjet.
Why ?
It's probable that that link above is a mistake or somehow 'assumed' new version is available via s-c.
The previous was & still is, it is called slimboat & no longer supported, screenshot

---

### Post by Mel_Blakey on 2016-02-18
I've downloaded the .deb package from the link above, double clicked it and software centre opens. But, it just goes round in circles and doesn't install.

After clicking install it asks for authentication then appears to go through the process. Doesn't install and starts back at the beginning.

Can anyone help?

---

### Post by shantiq on 2016-02-18
hi mel read my earlier post some dependencies are missing in the deb hence your problem probably

follow the [steps ]("http://ubuntuforums.org/showthread.php?t=2313957&p=13441405#post13441405")indicated and should be fine

---

### Post by Mel_Blakey on 2016-02-18
Hi
I tried the steps in your post and it still didn't install. Then I remembered to alter the file permissions and tick the '**Allow executing file as a program**' box. And Bob's Your Uncle...it installed!

Lets hope that it was worth it..


Thanks a lot.

---

### Post by shantiq on 2016-02-18
cool :]

---

### Post by Mel_Blakey on 2016-02-18
[COLOR=#008080]what I like MOST about our Ubuntu community  ...   exchanging tips  to make things better   ....   The World should take heed :][/COLOR][COLOR=#696969]

I agreeeee!
[/COLOR]

---

