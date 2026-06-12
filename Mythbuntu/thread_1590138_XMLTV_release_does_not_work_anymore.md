---
title: "XMLTV release does not work anymore"
date: 2010-10-07
forum: Mythbuntu
---

### Post by dibuntux on 2010-10-07
...but the nightly release is stated to be working on grab_it for italian channels.

Now the question is: how can I set my myth box to use the nightly release? And without getting mad & scrambling the whole system?

Thanks a lot in advance for any input on this!

---

### Post by dibuntux on 2010-10-08
ok, since no one is replying, I did it myself and turn it into this mini

HOWTO install nightly XMLTV

get [http://snapshot.xmltv.org](http://snapshot.xmltv.org) - Nightly snapshot 
create a dir xmltv-nightly and change to that dir
copy the Nightly snapshot file and uncompress it using tar xvzf xmltv-nightly.tgz
compile the program: perl Makefile.PL 
This should produce a listing that looks like this.

XMLTV.pm library and the filter programs such as tv_grep and tv_sort
are installed by default; here you choose grabbers for different
countries and front-ends for managing listings.
Grabber for Brazil (tv_grab_br)                                    [yes]
Grabber for Brazil NET Cable (tv_grab_br_net)                      [yes]
Grabber for Switzerland (tv_grab_ch_bluewin)                       [yes]
Alternative grabber for Britain (tv_grab_uk_rt)                    [yes]
Fast alternative grabber for the UK (tv_grab_uk_bleb)              [yes]
.... and so on. Find your country in the list and hopefully it will be marked "yes".
It now asks "Do you want to continue with this configuration ?" ; you actually don't need all those grabbers, but what the heck, just press RETURN for yes. 
Now compile and install the program with 
make ; -> verify the output is ok
sudo make install ; -> verify the output is ok

 Configuring XMLTV

Next we need to configure XMLTV. To do this run

tv_grab_it --configure

Now, for this grabber, you can individually select whether or not you want each channel. To select every channel (it's quicker to edit the configuration file in a text editor), type:

all

And it will configure itself to download every single channel it can.
Checking XMLTV actually works

To check it, simply run it.

tv_grab_it
Attention: to actually populate channels you have to run mythfilldatabase, and one note... you will see data starting from the day after!

GLTA

---

