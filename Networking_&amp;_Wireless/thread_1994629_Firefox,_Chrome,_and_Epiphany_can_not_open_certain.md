---
title: "Firefox, Chrome, and Epiphany can not open certain websites"
date: 2012-06-03
forum: Networking &amp; Wireless
---

### Post by AnaNefri on 2012-06-03
Hi all...

After updating ubuntu I got a problem: can not open certain websites and firefox being crashed when trying to open it. I thought It's just firefox problem, but then I installed chrome. When I try to open those websites on chrome, it says: Aw, snap always. And then I tried to install Epiphany, but when I try to open those website via epiphany, it's automatically quit. 

These are two of the websites:

-apachefriends forum
-stackoverflow

And yes,I have changed profile on each of browsers, but still didnt solve the problem.


What should I do?

Thank you so much.

-Ana

---

### Post by sanderj on 2012-06-03
Open a terminal, and type "firefox" to start firefox from there. If/when it crashes, you can (hopefully) see more info in the terminal.

Oh, you have fully updated your system? Run:

```
sudo apt-get update
sudo apt-get upgrade

```

HTH

---

### Post by AnaNefri on 2012-06-03
Yes, I have done upgrading and updating completly.

And this what I got in terminal when it crashes


(crashreporter:2769): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",


what does than mean?

---

### Post by sanderj on 2012-06-03
I don't know, but you did google it?

---

### Post by shafi.dude99 on 2012-06-03
[FONT=Courier New]try this command from shell

sudo apt-get install gtk2-engines-pixbuf[/FONT]

---

### Post by vasa1 on 2012-06-03
And just to be clear it is only a few sites or is Firefox just crashing all the time?

---

### Post by vasa1 on 2012-06-03
> **shafi.dude99 said:**
> [FONT=Courier New]try this command from shell

sudo apt-get install gtk2-engines-pixbuf[/FONT]
I don't have that. I just have:
```
gtk2-engines					install
gtk2-engines-murrine				install
gtk2-engines-xfce				install
gtk3-engines-unico				install

```
and Firefox and Chrome open those sites without problems.

What does "[FONT="Courier New"]gtk2-engines-pixbuf[/FONT]" do?

---

### Post by AnaNefri on 2012-06-03
> **shafi.dude99 said:**
> [FONT=Courier New]try this command from shell

sudo apt-get install gtk2-engines-pixbuf[/FONT]


I did..but still the same :(

---

### Post by traditionalist on 2012-06-03
> **AnaNefri said:**
> Hi all...

After updating ubuntu I got a problem: can not open certain websites and firefox being crashed when trying to open it. I thought It's just firefox problem, but then I installed chrome. When I try to open those websites on chrome, it says: Aw, snap always. And then I tried to install Epiphany, but when I try to open those website via epiphany, it's automatically quit. 

These are two of the websites:

-apachefriends forum
-stackoverflow

And yes,I have changed profile on each of browsers, but still didnt solve the problem.


What should I do?

Thank you so much.

-Ana

The theme engine is not accessible.  Set Firefox to use its own colours and see if that helps;

[[IMG]http://img842.imageshack.us/img842/8413/selection001ns.th.png[/IMG]]("http://img842.imageshack.us/i/selection001ns.png/")

You can install the gtk2 engine here;

[http://packages.ubuntu.com/precise/gtk2-engines-pixbuf](http://packages.ubuntu.com/precise/gtk2-engines-pixbuf)

what version of Ubuntu are you using?

---

### Post by AnaNefri on 2012-06-03
> **vasa1 said:**
> And just to be clear it is only a few sites or is Firefox just crashing all the time?


Actually Firefox also chrasing when I opening add-ons menu. But why I also cant open those same websites on chrome and epiphany if it just firefox add-ons?

---

