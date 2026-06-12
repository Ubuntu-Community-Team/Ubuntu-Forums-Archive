---
title: "Traverso installation fails"
date: 2019-04-27
forum: Multimedia Software
---

### Post by jpsullaz on 2019-04-27
Hello, my first post here working with a new Ubuntu machine. Trying to install Traverso DAW and got up to the point of 'make' but am getting make: ***** No targets specified and no makefile found.  Stop. All prereqs went fine up to that point. I was following the video here [https://www.youtube.com/watch?v=9RU07I8hABE](https://www.youtube.com/watch?v=9RU07I8hABE).

Have used Ubuntu before but has been many years, currently want to build a Linux audio workstation. 

Thanks,

JP

---

### Post by coffeecat on 2019-04-27
Why not simply install traverso from the Ubuntu repositories and save yourself hassle, heartache and frustration? Compiling from source is usually a last resort for software installation.

If you post details of which release of Ubuntu you are using, forum members will be able to advise how to use the package manager, if you need that information.

---

### Post by remonsijrier on 2019-04-28
> **jpsullaz said:**
> Hello, my first post here working with a new Ubuntu machine. Trying to install Traverso DAW and got up to the point of 'make' but am getting make: ***** No targets specified and no makefile found.  Stop. All prereqs went fine up to that point. I was following the video here [https://www.youtube.com/watch?v=9RU07I8hABE](https://www.youtube.com/watch?v=9RU07I8hABE).

Have used Ubuntu before but has been many years, currently want to build a Linux audio workstation. 

Thanks,

JP

As noted, it is much easier to install Traverso using apt-get or from the software centre

Due changes most compile tutorials for compiling Traverso-DAW from source no longer work. On [https://traverso-daw.org](https://traverso-daw.org) will be an updated ' how to compile from source '  soon in order to test out the development version.

---

### Post by jpsullaz on 2019-04-29
Thanks for the advice, I don't see Traverso listed in the app center but will try to install it that way. Using 18.04.

---

### Post by Rubi1200 on 2019-04-29
The package is available for 18.04:
[https://packages.ubuntu.com/bionic/traverso](https://packages.ubuntu.com/bionic/traverso)

You can either add via the terminal with ```
sudo apt-get install traverso
``` or you can install the classic package manager Synaptic ```
sudo apt-get install synaptic
``` and then search for and add it from there.

Personally, I recommend installing Synaptic first and then using that for package management. Synaptic has everything in there and is very easy to use.

---

### Post by jpsullaz on 2019-04-29
Thanks, my question would be the need for all the prereqs mentioned in the video?

---

### Post by Rubi1200 on 2019-04-29
If you check the link I posted to Bionic packages it shows all the dependencies. Those not already installed would be pulled in with the main package when downloading.

---

### Post by jpsullaz on 2019-05-09
> **Rubi1200 said:**
> The package is available for 18.04:
[https://packages.ubuntu.com/bionic/traverso](https://packages.ubuntu.com/bionic/traverso)

You can either add via the terminal with ```
sudo apt-get install traverso
``` or you can install the classic package manager Synaptic ```
sudo apt-get install synaptic
``` and then search for and add it from there.

Personally, I recommend installing Synaptic first and then using that for package management. Synaptic has everything in there and is very easy to use.

Thanks, I did it that way and worked fine. The links to the user manual do not seem to work is there another place I can get one?

---

### Post by Rubi1200 on 2019-05-09
Online here:
[https://traverso-daw.org/products/](https://traverso-daw.org/products/)

Happy to hear things worked out.

Please mark this thread Solved using the thread tools at the top of the first post.

Goof luck!

---

