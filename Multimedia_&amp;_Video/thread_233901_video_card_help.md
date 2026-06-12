---
title: "video card help"
date: 2006-08-10
forum: Multimedia &amp; Video
---

### Post by L_o_N_e_R on 2006-08-10
82830 CGC [Chipset Graphics

thats what it shows on the device manager but im not sure if thats my video card....

i need 1 things

another way to check video cards

can any1 help me?

---

### Post by tseliot on 2006-08-10
post the output of this command:
```
lspci | grep VGA
```

and if that doesn't display anything try this:
```
lspci
```

---

### Post by Jussi Kukkonen on 2006-08-10
> **L_o_N_e_R said:**
> can any1 help me?

You'll get more help if you stop posting so much (you have almost 50 posts in a very short time), and think a little longer about how you present your problems and questions (this post doesn't tell me very well what you want...).

Anyway, run 
```
lspci -v
```
to see information on your cards (and other things in the PCI bus). If you cant find your video card, paste the output here.

---

### Post by Jussi Kukkonen on 2006-08-10
> **Jussi Kukkonen said:**
> You'll get more help if you stop posting so much (you have almost 50 posts in a very short time), and think a little longer about how you present your problems and questions (this post doesn't tell me very well what you want...).

Anyway, run 
```
lspci -v
```
to see information on your cards (and other things in the PCI bus). If you cant find your video card, paste the output here.


Looking at it again the above was probably not warranted -- I just happened to see several posts from you and several (other) posts that were quite hard to decipher and jumped to conclusions. Sorry about that.

---

### Post by L_o_N_e_R on 2006-08-10
0000:00:02.0 VGA compatible controller: Intel Corporation 82830 CGC [Chipset Graphics Controller] (rev 04)


yup thats it :)

thnx guys

now to find drivers.....sigh

edit how do i install drivers?

---

### Post by L_o_N_e_R on 2006-08-10
[http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=669&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadfinder.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=669&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

which one do i pick?

---

### Post by L_o_N_e_R on 2006-08-10
heh i also need to know it its compatable with ubuntu

and maybe also installation instructions?

---

### Post by L_o_N_e_R on 2006-08-10
1.  Install Linux

2.  Log in as root or as a superuser

3.  Install kernel headers

    	a.  For Red Hat versions, this is normally on CD2:
	    /RedHat/RPMS/kernel-source-2.4.18-3.i386.rpm

    	b.  Alternately, load your kernel config file, 
	    save the config, and run &#8220;make dep&#8221; 

4.  Extract the downloaded files:
        
	a.  tar &#8211;zxvf 20030106-i386-Linux.tar.gz

5.  Ensure X Windows is not running

6.  cd dripkg

7.  ./install.sh

8.  Follow the prompts; most users should be able to press
    &#8220;Enter&#8221; at each prompt

thats what i found in the readme tor the tar.gz file

questions
1 do i have to put kernel headers
2 whats x windows?

---

### Post by tseliot on 2006-08-11
L_o_N_e_R
please stop starting new threads for the same problem.

I'm merging your threads

---

### Post by tseliot on 2006-08-11
Open your xorg.conf:

```
sudo nano -w /etc/X11/xorg.conf
```

Get to the Section Device and set the driver to
```
i810
```

In this way you will use the driver for your card.

Then log out and press CTRL+ALT+Backspace.
And log in again.

---

### Post by L_o_N_e_R on 2006-08-11
i do that before i update drivers?

---

### Post by tseliot on 2006-08-11
> **L_o_N_e_R said:**
> i do that before i update drivers?

No. Just do what I said and you're done. No further step is required.

---

