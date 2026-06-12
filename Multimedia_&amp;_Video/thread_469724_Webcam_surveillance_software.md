---
title: "Webcam surveillance software?"
date: 2007-06-10
forum: Multimedia &amp; Video
---

### Post by daller on 2007-06-10
Hi there,

I'm setting up some webcams to serve as surveillance in our shop (€100, compared to over €1000 for a professional system...)

Is there some surveillance-specific linux software out there, that would work with webcams?

To start with, I'm trying to get 4 webcams up and running on the same machine...

It should show in a QUAD-screen 2x2 webcams, and individual webcams should be selectable, so that the zoom to the whole screen...

Any ideas?

---

### Post by rklauco on 2007-06-10
Try this:
[http://www.zoneminder.com/]("http://www.zoneminder.com/")
Works great.

---

### Post by daller on 2007-06-11
Hi there,

Thank you! - One question though!

How do I start the application?

```
daniel@daniel-laptop:~$ zoneminder
bash: zoneminder: command not found
daniel@daniel-laptop:~$
```

I'm running "Kubuntu 7.10 - Gutsy Gibbon" (It has Zoneminder in the Universe-repo)

---

### Post by mohnkern on 2007-06-11
You'll probably want to read the docs, Zoneminder is a set of modules that you have to activate:

[http://www.zoneminder.com/fileadmin/downloads/README.html](http://www.zoneminder.com/fileadmin/downloads/README.html)

---

### Post by rklauco on 2007-06-11
There is an easier way - download the live CD and try it first, then get the modules and go through the installation process...

---

### Post by daller on 2007-06-12
I've installed Kubuntu 7.10 - Gutsy Gibbon (Current development)

I can install zoneminder by running: "sudo apt-get install zoneminder"

It finds all the needed packages, and installs!

Now, after installation, what do I do?

How do I start the GUI?

---

### Post by flat4 on 2007-06-15
> **daller said:**
> I've installed Kubuntu 7.10 - Gutsy Gibbon (Current development)

I can install zoneminder by running: "sudo apt-get install zoneminder"

It finds all the needed packages, and installs!

Now, after installation, what do I do?

How do I start the GUI?


Man i have been trying to do that for a while, trying to get "apt-get" to get and install the software but my damn sources.list keeps asking for a cd even though there is no line for the cd to be indexed, ANYWAY!!

You use your web browser to configure zone minder. You have to modify apache so it will see zoneminder.

Go to the zoneminder site [www.zoneminder.com ]("http://www.zoneminder.com") use the wiki on how to modify your config file.

---

### Post by Stian1979 on 2007-07-28
> **daller said:**
> 

I'm running "Kubuntu 7.10 - Gutsy Gibbon" (It has Zoneminder in the Universe-repo)

How do I enable the Universe repo?

I downloaded kubuntu 7.04 because instaling zoneminder from source did not work and the packages in the fedora repos seams not to work well.

---

### Post by Stian1979 on 2007-08-01
Newer mind, I got the zoneminder package installed, but I switched from "k"ubuntu to debian, I gues it's the same package.

If annybody figured out how to load zoneminder to firefox I would like to know

---

### Post by flat4 on 2007-08-01
> **Stian1979 said:**
> Newer mind, I got the zoneminder package installed, but I switched from "k"ubuntu to debian, I gues it's the same package.

If annybody figured out how to load zoneminder to firefox I would like to know

What exactly do you need help in firefox?

---

### Post by Stian1979 on 2007-08-02
> **flat4 said:**
> What exactly do you need help in firefox?

I dont nead help in firefox. I nead help with zoneminder.

> # Current version of ZoneMinder
ZM_VERSION=1.22.3

# Path to build directory, used mostly for finding DB upgrade scripts
ZM_PATH_BUILD=/tmp/buildd/zoneminder-1.22.3

# Build time, used to record when to trigger various checks
ZM_TIME_BUILD=1185700104

# Path to ZoneMinder binaries
ZM_PATH_BIN=/usr/bin

# Path to ZoneMinder libraries (none at present, for future use)
ZM_PATH_LIB=/usr/lib

# Path to ZoneMinder configuration (this file only at present)
ZM_PATH_CONF=/etc/zm

# Path to ZoneMinder web files
ZM_PATH_WEB=/usr/share/zoneminder

# Path to ZoneMinder cgi files
ZM_PATH_CGI=/usr/lib/cgi-bin

# Username and group that web daemon (httpd/apache) runs as
ZM_WEB_USER=www-data
ZM_WEB_GROUP=www-data

# ZoneMinder database hostname or ip address
ZM_DB_HOST=localhost

# ZoneMinder database name
ZM_DB_NAME=zm

# ZoneMinder database user
ZM_DB_USER=zmuser

# ZoneMinder database password
ZM_DB_PASS=zmpass

Typing localhost in my browser just get me the apashe report file not found on this server

---

### Post by flat4 on 2007-08-02
i would get the same error, I installed it on a  ubuntu 7.04 server, then I found this great how to and after i followed the steps it worked for me.

[http://www.zoneminder.com/forums/viewtopic.php?t=9747]("http://www.zoneminder.com/forums/viewtopic.php?t=9747")

Of course this is for an ubuntu install but i bet you can extract info to help you get it going.

PS. to me it looks like you have not added the zoneminder entry to the apache.conf.

---

### Post by shtong on 2008-05-22
> **rklauco said:**
> Try this:
[http://www.zoneminder.com/]("http://www.zoneminder.com/")
Works great.

ok i got the archive from there and wtf do i do now? i should mention that im new to ubuntu and i have no ideea what to do! if there is anyone that can help me please do so!

thank you!

---

### Post by rklauco on 2008-05-22
> **shtong said:**
> ok i got the archive from there and wtf do i do now? i should mention that im new to ubuntu and i have no ideea what to do! if there is anyone that can help me please do so!

thank you!
Well, I do not realy thing that using abbreviations like WTF will help you to move forward.
At least I am not willing to answer such rude post.

---

### Post by Terry of Astoria on 2008-05-27
I have put together a HOWTO for installing zoneminder on Ubuntu 7.10 Gutsy Gibbon. See it here:
[http://threeeighthsspacer.com/blog/2008/05/15/ubuntu-zoneminder-install-gutsy-710/](http://threeeighthsspacer.com/blog/2008/05/15/ubuntu-zoneminder-install-gutsy-710/) 
    I'm sure it's quite enough to make your blood boil, when the instructions are not easy to find or aren't clear. I'm sorry that you haven't gotten any helpful response here so far. I don't know if there's already a package for Hardy Heron yet. I suggest you use Ubuntu 7.10. There's a package for it, and if you try, perhaps following the instructions I linked to, you may achieve success. 
   As someone alluded to above, once Zoneminder is installed, you can access the Zoneminder control panel with a web browser. If it is installed on your local computer try [http://localhost/zm](http://localhost/zm) and if it's another computer, replace "localhost" with the ip address of that computer.

---

### Post by G|N| on 2008-05-27
Another good and more easy alternative is "Motion":

[http://infectedproject.wordpress.com/2007/06/26/set-up-a-webcam-security-system/](http://infectedproject.wordpress.com/2007/06/26/set-up-a-webcam-security-system/)

---

### Post by Bubba64 on 2008-05-27
[QUOTE=flat4;2849209]Man i have been trying to do that for a while, trying to get "apt-get" to get and install the software but my damn sources.list keeps asking for a cd even though there is no line for the cd to be indexed, ANYWAY!!


This may be a moot point but regarding the mention of CD, have you gone to software sources located in administrative or synaptic and checked if the CD portion is still ticked on, it should be off if your installed, and the resources you do want are on. Flat 4 you must be a musician can I call you tritone

---

