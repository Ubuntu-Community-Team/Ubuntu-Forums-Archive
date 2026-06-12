---
title: "[SOLVED] Acer Aspire One Netbook, No Wirless"
date: 2008-12-25
forum: Networking &amp; Wireless
---

### Post by doubad on 2008-12-25
I just installed intrpid and got rid of windows on this netbook. Wirless won't work and I've been sifting through "wireless problems with edgy/breezy" and I'm getting sick of it.  Does anyone have any updated info on how to get wireless on my netbook?

---

### Post by doubad on 2008-12-26
Anyone? 
Should I be getting madwifi?

---

### Post by Jakey_TheSnake on 2008-12-26
I have the same problem. 

The wireless card is recognised and working with my Linpus Linux Lite which came on the machine, but is not recognised by default with my Ubuntu installation (it's dual boot currently). 

Any help would be greatly appreciated. 

@doubad: please email me at [email]clampstand@gmail.com[/email] if you find a fix, or post it here. I shall be looking into it with more detail when I get home later tonight, or tomorrow - will report back. 

Mod please do not edit to exclude my email address, I do not care for spam with that account.

---

### Post by Jakey_TheSnake on 2008-12-26
Have it fixed now. 


Download this wireless driver: [http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz](http://snapshots.madwifi-project.org/madwifi-hal-0.10.5.6/madwifi-hal-0.10.5.6-r3879-20081204.tar.gz) 

Move it to your Documents folder and extract. 

Open up a Terminal (Applications > Accessories > Terminal)

Type:

```
cd /home/username/Documents/madwifi-hal-0.10.5.6-r3879-20081204
```

Press enter. Then type:

```
make
```

Will take a couple of minutes, wait until you get the correct prompt again. 

Then type:

```
sudo make install
```

Let it do it's stuff, then:

```
modprobe ath_pci
```

Restart laptop, then when you click your networks icon you should get that beautiful list of wireless networks to connect to. 

Hope this helps, 

- Jake.

NB: how do you like the Aspire One so far? I like it, pretty damn neat, need to get my compiz working though =\

---

### Post by doubad on 2008-12-27
It's so nice to come home after a long day and someone has solved the problem for you. Thank you so much! You've fixed it.


I love my little aspire, this is my first laptop. I've never seen the point of owning a laptop until these netbooks came out.

Thanks again!

---

### Post by Aatish1976 on 2009-01-27
Hi

I have just installed Ubuntu on my acer one netbook, but the wireless does not work, so after pulling my hairout i came acroos this website and this help, and i was so excited until i came across this issue. I have have followed the instructions but it does not seem to work for for me when i type the first command it says no such file or directory, This is what i did.

downloaded [http://snapshots.madwifi-project.org...0081204.tar.gz](http://snapshots.madwifi-project.org...0081204.tar.gz)
on a usb stick, unziped it and had a file clled madwifi-hal-0.10.5.6-r3879-20081204  I then placed the usb in my acer netbook usb slot and copied it in  Ubuntu's places then selected Documents.
then loaded Terminal and typed cd /home/username/Documents/madwifi-hal-0.10.5.6-r3879-20081204  then press enter
it says No such file or directory.
I have tried with space after cd and with no space after cd but i still get no joy.

I am very new to this so please help me i bought a external dvd drive so i can install ubuntu on it as it only comes with Acer version on linux, Please help as i do not want to install acer linux on it .

Thank you

Kibria

---

### Post by doubad on 2009-01-27
I hope you remembered to replace the "username" part of it with your username.

But, what I did is rename the folder that comes from the tar.gz file to something easier.
So mine looked like something like this
cd /home/darryl/Documents/madwifi
then I followed the instructions above.

---

### Post by Jakey_TheSnake on 2009-01-31
> **Jakey_TheSnake][QUOTE=Aatish1976]Please have a look at this post again, as i am having some problem.

I am really sorry to send you a private email, but i need help.

thank you 
kibria[/QUOTE]

No problem said:**
> jb.dude@gmail.com[/email]

So you have an Acer Aspire One, and the wireless is not working? have you followed the commands provided in the post? 

The first command is ```
cd /home/username/Documents/madwifi-hal-0.10.5.6-r3879-20081204
```

You need to replace where it says "username" with your own username. This is the one you use to log in. If you don't know it you can find out by going to System > Preferences > About Me, and then in the top right it will tell you your username. 

Hope this helps, 

Jake

I responded to your pm. 

Also, the purchase of an external CD/DVD drive was unnecessary, as Ubuntu can be installed from a USB drive.

---

