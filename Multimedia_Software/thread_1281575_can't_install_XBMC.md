---
title: "can't install XBMC"
date: 2009-10-03
forum: Multimedia Software
---

### Post by darrude on 2009-10-03
Hi,

I'm really struggling installing XBMC on my acer revo.

I have followed this tutorial [http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step](http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu_with_a_minimal_installation_step-by-step) but when I get to trying to install XBMC from syamptic package manager, I get the following error:

 Depends: xbmc-common but it is not going to be installed
 Depends: xbmc-skin-pm3-hd but it is not going to be installed
 Depends: xbmc-web-pm3 but it is not going to be installed

So I then tried to install xbmc-standalone first and got the same error.

My next course of action was to install xbmc-common,  this came up with the following error:

xbmc-common:
 Depends: python-sqlite but it is not going to be installed
 Depends: libcurl4-openssl-dev but it is not going to be installed

So I though ok, i'll try to install  python-sqlite, but this gave the following error:

python-sqlite:
  Depends: python (<2.6) but 2.6.2-0ubuntu1 is to be installed

and now i'm stuck, when I search python I get loads for results, I have installed python 2.4, python 2.5 and python 2.6, but it still won't install.

Now i'm really stuck, 

Hope someone can help.

Many Thanks,

Darren

---

### Post by aherst on 2009-11-07
I'm having the same problem.

Adam

---

### Post by darrude on 2009-11-08
Hi Adam,

I have no idea why, but mine suddenly started working!  

i wish i could tell you why!

Darren.

---

### Post by r2d2blue on 2009-12-24
Hi,
I just installed XBMC on my Acer Revo 3610.
Took no time.

Do this...

** Installing XBMC Ubuntu 9.10 Karmic or higher**

 If you are using Ubuntu 9.10 or higher, you have the option of a more streamlined install. Load the terminal window and issue the following (The $ is a standard substitute for your terminal prompt): 
  	 	     $ sudo add-apt-repository ppa:team-xbmc
     $ sudo apt-get update
     $ sudo apt-get install xbmc
     $ sudo apt-get update
   
You do not need to add the XBMC Repo nor the PPA Keys.  XBMC is already installed. 





All this from here...
[http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu%2C_a_Step-by-Step_Guide](http://xbmc.org/wiki/?title=HOW-TO_install_XBMC_for_Linux_on_Ubuntu%2C_a_Step-by-Step_Guide)




To get SVN plug-ins...watch this tutorial...


[http://www.youtube.com/watch?v=D2NNg2OCLVM](http://www.youtube.com/watch?v=D2NNg2OCLVM)



-r2

---

### Post by tonesteroc on 2011-09-13
after all that stuff, sudo apt-get build-dep xbmc fixed it! then sudo apt-get install xbmc ;)

---

### Post by overdrank on 2011-09-13
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

