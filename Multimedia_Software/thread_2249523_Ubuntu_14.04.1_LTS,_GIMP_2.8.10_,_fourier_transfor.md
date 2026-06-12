---
title: "Ubuntu 14.04.1 LTS, GIMP 2.8.10 , fourier transform plug-in"
date: 2014-10-22
forum: Multimedia Software
---

### Post by dale9 on 2014-10-22
having troubling with make and make install of the fourier transform  plug-in for gimp 

[http://chidge.net/?m=stuff&o=howtos&p=fft](http://chidge.net/?m=stuff&o=howtos&p=fft) 

the make error I get is 
make: Nothing to be done for `all'. 

if I (make install) after the make error, there is no error and it  creates a binary, but the filers don't show up under filters/generic  like the website above says 

the binary is call fourier, if I try to run it I get the error 
bash: ./fourier: cannot execute binary file: Exec format error 

there are errors gimp-2.0 --install-bin cp fourier /home/dale/.gimp2.8/plugins
says 

No command 'gimp-2.0' found, did you mean:
 Command 'gimp-2.8' from package 'gimp' (main)
gimp-2.0: command not found

Unknown option --install-bin comes up if I replace 2.0 with 2.8

I think I have all the libraries, there are no errors that libraries are  needed 

I am using this version of Ubuntu Linux 
Distributor ID:    Ubuntu 
Description:    Ubuntu 14.04.1 LTS 
Release:    14.04 
Codename:    trusty 

and GIMP 2.8.10 

where can I get Gimp 2.0 or an updated version of the plug-in


I'll be googling around in the mean time...

---

### Post by steeldriver on 2014-10-22
Hello and welcome to the forums

Try running

```

make clean

```

to remove any previously compiled files and then running

```

make 

```

again.

---

### Post by mc4man on 2014-10-22
Did you install libgimp2.0-dev before the make, make install?
That's where /usr/bin/gimptool-2.0 comes from 
(- then the make install will install fourier to ~/.gimp-2.8/plug-ins/

Ex.
~/Downloads/fourier-0.4.3$ make install
gimptool-2.0 --install-bin fourier
cp fourier /home/doug/.gimp-2.8/plug-ins

---

### Post by dale9 on 2014-10-22
thanks very much, the help comes fast here, I'm kind of a 15 year or so newbie to Ubuntu but I think I'll browse and contribute now

thanks very much again

now I can study up on Gimp plugins, scripting and python
might not get anywhere but it will keep me busy

---

### Post by dale9 on 2014-10-22
steel driver's reply got it to show up and run, but it shows up somewhere close to 50% L* grey, the inverse works, I can do a brightness and contrast adjustment, guess I will study from here

---

### Post by dale9 on 2014-10-22
it shows up somewhere close to 50% L* grey, the inverse works, I can do  a brightness and contrast adjustment, guess I will study from here

thanks again

---

