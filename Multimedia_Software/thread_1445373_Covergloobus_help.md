---
title: "Covergloobus help?"
date: 2010-04-02
forum: Multimedia Software
---

### Post by Cam42 on 2010-04-02
I can't get Covergloobus to run. I've uninstalled it, reinstalled it, tried compiling from source, and nothing works. Help?

---

### Post by tareksobh on 2010-04-15
> **Cam42 said:**
> I can't get Covergloobus to run. I've uninstalled it, reinstalled it, tried compiling from source, and nothing works. Help?

If you have python-gtk libraries already installed, try typing this in the Terminal. It worked for me.

```
sudo add-apt-repository ppa:gloobus-dev/covergloobus
```

```
sudo apt-get update && sudo apt-get install covergloobus
```

I got this from OMG! Ubuntu! Blog [HERE]("http://www.omgubuntu.co.uk/2010/02/covergloobus-16-wow-lives-up-to-its.html")

If you don't have python-gtk, get it by typing this in the Terminal:

```
sudo apt-get install python-gtk2
```

Good Luck :)

---

### Post by Cam42 on 2010-04-16
I got it figured out, I ran the cover art on docky option, which conflicted with Docky, and crashed. Had to start it without docky on, and then edit out that setting.

---

