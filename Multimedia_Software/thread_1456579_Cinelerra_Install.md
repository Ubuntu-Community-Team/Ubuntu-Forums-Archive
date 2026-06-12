---
title: "Cinelerra Install"
date: 2010-04-17
forum: Multimedia Software
---

### Post by Skifire on 2010-04-17
I give, I can't figure out how to get the dependencies installed.

mark@mark-desktop:~$ sudo apt-get install cinelerra
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  cinelerra: Depends: libcinelerra (= 2.1.1+git20100325) but it is not going to be installed
             Depends: libfaad0 (>= 2.6.1) but it is not installable
             Depends: libmjpegtools0c2a (>= 1:1.8.0) but it is not installable
             Depends: libraw1394-8 but it is not installable
             Depends: libx264-59 (>= 1:0.svn20080408) but it is not installable
E: Broken packages


Thanks all, 
Mark

---

### Post by I8NY on 2010-04-17
did you go look at the how to on the site [here]("http://cinelerra.org/getting_cinelerra.php#ubuntu")?  after adding the repository go to the package manager and search for Cinelerra, install it and it will install with other package dependencies.  After that it should make a icon in applications and it will work.  This worked for me i hope it does for you.

---

### Post by hayden92 on 2010-04-19
Hi Skifire,

I did have the same issue.  What I did wrong was to install
```
http://akirad.cinelerra.org/pool/addakirad.deb
```

Before adding the line:
```
deb http://akirad.cinelerra.org akirad-<*YOURVERSION*> main
```

Did you install these in the right order?

Hope that helps,

Hayden M

---

