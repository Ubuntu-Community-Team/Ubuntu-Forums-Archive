---
title: "Mythtv. No UPnP backends"
date: 2010-01-13
forum: Mythbuntu
---

### Post by kunks112 on 2010-01-13
Hi

I have installed Mythtv three times. Everytime I try to set up the back end, it takes me to the language screen, I choose english. 
Then I hit enter and I get a "No UPnP backends found"

I hit ok

Under hostname I put localhost and keep the password empty

In part 2 of the configuration I do not check the custom identifier preferences or server wakeup

Hit Enter and it says cannot login to database

How do I properly install and use mythtv?

Mike

---

### Post by SiHa on 2010-01-13
> **kunks112 said:**
> Hi

I have installed Mythtv three times. Everytime I try to set up the back end, it takes me to the language screen, I choose english. 
Then I hit enter and I get a "No UPnP backends found"

I hit ok

Under hostname I put localhost and keep the password empty

In part 2 of the configuration I do not check the custom identifier preferences or server wakeup

Hit Enter and it says cannot login to database

How do I properly install and use mythtv?

Mike

I think you're actually trying to run the frontend. To setup the backend run mythtv-setup.

---

### Post by kunks112 on 2010-01-13
I have, from terminal I typed mythtv-setup.
The above problem persists

---

### Post by SiHa on 2010-01-14
Well I'm confused then. The errors you describe are what happens when you attempt to run the frontend when the backend is not setup properly. When you run the backend setup (mythtv-setup), there should be a menu: General Settings, Capture Cards, Video sources, Input Connections etc...

Do you get this?

What do you have in all the boxes of general setup?

Is the mysql password right? It's stored in (IIRC) /etc/mythtv/mysql.txt.

Just a thought - maybe a daft question, are you typing```
mythtv-setup
``` (no spaces) or ```
mythtv -setup
```

It should be the first one.

---

### Post by Mr Nemo on 2010-01-14
I think 'sudo aptitude install mythtv-backend' might work.

---

### Post by kunks112 on 2010-01-20
Re-installed mythtv
with no space I type mythtv-setup, a box appears saying 
"Mythbackend must be closed before continuing. Is it OK to close any currently running mythbackend processes?"
Options( Cancel, OK )

Cancel Cancels, OK gives previously stated problem.

I did try sudo aptitude install mythtv-setup, but that did not work

Thanks for replies

---

### Post by ReddogOne on 2010-01-20
When you run the setup did it ask you something like if you wanted the backend to be share or visible or something like that. If it did say yes. This should be enough.

Try it when you have the front end running on the machine you are using as a backend.

Check in the general setting of the backend that the you have the ip for the machine itself and not localhost or 127....

---

### Post by radnor on 2010-01-20
> **kunks112 said:**
> Under hostname I put localhost and keep the [COLOR="Red"]**password empty**[/COLOR]

I'm a noob on this but...  in either /home/mike/.mythtv or /home/mythtv/.mythtv look for mysql.txt  look for the password to mysql.  enter that when you setup the backend with myth-setup and try again.

I had the same error when I added a RFE to my setup and had the wrong password (from the install).  As soon as I changed that, it worked without problems.

---

### Post by kunks112 on 2010-01-22
> **ReddogOne said:**
> When you run the setup did it ask you something like if you wanted the backend to be share or visible or something like that. If it did say yes. This should be enough.

Try it when you have the front end running on the machine you are using as a backend.

Check in the general setting of the backend that the you have the ip for the machine itself and not localhost or 127....

When I try to run front end, the exact screens as I first mentioned appeared.

So no matter if I try to config backend or run frontend, the same screens and errors appear.

I have re-installed mythtv 3 times now witht the exact same problem.

I cant get it to work.

---

### Post by kunks112 on 2010-01-22
> **radnor said:**
> I'm a noob on this but...  in either /home/mike/.mythtv or /home/mythtv/.mythtv look for mysql.txt  look for the password to mysql.  enter that when you setup the backend with myth-setup and try again.

I had the same error when I added a RFE to my setup and had the wrong password (from the install).  As soon as I changed that, it worked without problems.

No change

---

### Post by ReddogOne on 2010-01-25
> **kunks112 said:**
> I cant get it to work.

Do what [this]("http://parker1.co.uk/mythtv_ubuntu.php") page says and see what happens.

Also I noticed recently (without me asking) my firewall seems to have re-configured itself. Try stopping it (I used firestarted, I think it was called).

---

### Post by kunks112 on 2010-01-27
I initially followed this guide. However when I do 
```
sudo apt-get install dvb-apps dvbstream

``` 
I receive the message that "E: Couldn't find package dvb-apps"

other then that, i followed the rest of the guide and i have the same initial issue as i originally posted.

I think mythtv is just not meant to be for me.

Thanks

---

