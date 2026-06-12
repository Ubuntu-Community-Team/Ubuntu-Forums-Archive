---
title: "Openshot wont Install"
date: 2012-06-27
forum: Multimedia Software
---

### Post by lobbers66 on 2012-06-27
I am trying to install Openshot on Ubuntu 12.04 but get the following.

The following packages have unmet dependencies:
openshot: Depends: python (>= 2.5) but 2.7.3-0ubuntu2 is to be installed

I recently upgraded from 11.10 and had the same problem there as well.

Any ideas would be appreciated. Do not want to start from scratch and reinstall 12.04. I think problem might be related to Kdenlive that I tried to install some time back.
Thanks

---

### Post by nipunshakya on 2012-06-27
what version of python is installed in your machine??? to see that copy the code in terminal and paste the output here:
```
python --version
```I guess the python version is incompatible for your installation as u said u upgraded from 11.10

---

### Post by lobbers66 on 2012-06-27
Python 2.7.3

---

### Post by nipunshakya on 2012-06-27
okay.. someone has similar issues and a question on the following link:
[http://www.zoringroup.com/forum/viewtopic.php?f=5&t=2308](http://www.zoringroup.com/forum/viewtopic.php?f=5&t=2308)
 a solution is given as well, might worth try...

---

### Post by lobbers66 on 2012-06-27
Thanks,
Have tried loading openshot .deb package using Gdebi (as suggested) and get the following error 
Error: Cannot install 'python-mlt3'

When I try to install python-mlt3 I get

sudo apt-get install python-mlt3
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 python-mlt3 : Depends: libmlt4 but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Think this is permissions problem, will look at them later.
Thanks for your help.

---

### Post by nipunshakya on 2012-06-27
i guess there is some problem with your upgrade to 12.04 because i have openshot installed in my machine recently without any errors... The last line of your error might highlight what i meant...

---

