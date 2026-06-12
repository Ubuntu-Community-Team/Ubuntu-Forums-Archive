---
title: "Automatic Connection (wireless)"
date: 2010-05-27
forum: Networking &amp; Wireless
---

### Post by Jon_ on 2010-05-27
Hello, 
  Just a quick question, my connections are working when I manually click to make the connection but just wondering why it will not connect automatically when I boot up. I have it checked to automatically connect but it doesn't. 

It is a hidden connection by the way but it does connect when I goto hidden connections and click connect. I am just wondering why it wont do it automatically.



Any ideas?

---

### Post by b k on 2010-05-27
> **Jon_ said:**
> Hello, 
  Just a quick question, my connections are working when I manually click to make the connection but just wondering why it will not connect automatically when I boot up. I have it checked to automatically connect but it doesn't. 

It is a hidden connection by the way but it does connect when I goto hidden connections and click connect. I am just wondering why it wont do it automatically.



Any ideas?

Hi there,if you are set up to auto login to your user account on bootup, then try this:

Go to *System*, *Administration*, *Login Screen*, *Unlock* and then [COLOR=Blue]uncheck/untick[/COLOR] Log in as xxxxxxx automatically and then tick Show the screen for choosing who will log in.

This should work for you but then every time upon bootup you will have to enter your password to log in to your user account.

Hope the info is of some help.

---

### Post by Jon_ on 2010-05-27
Thanks, I'll give that a try.

---

### Post by kerry_s on 2010-05-27
> **Jon_ said:**
> Hello, 
  Just a quick question, my connections are working when I manually click to make the connection but just wondering why it will not connect automatically when I boot up. I have it checked to automatically connect but it doesn't. 

It is a hidden connection by the way but it does connect when I goto hidden connections and click connect. I am just wondering why it wont do it automatically.



Any ideas?

right click the wifi icon-> edit connections-> wireless-> edit
check "available to all users"

---

### Post by b k on 2010-05-27
Ageed, I think try post #4 first and then if problem is still not resolved then try combination of posts # 2 and #4 :)

Good luck

---

### Post by Jon_ on 2010-05-27
I tried both and didn't work. I had to manually connect again. Any other ideas?

---

### Post by kerry_s on 2010-05-27
did you set a password?

if you did, delete the password. only put the key for the network, just leave the keyring password blank.

applications-> accessories-> passwords & encryption

---

### Post by Jon_ on 2010-05-27
That might be the problem. I went to the password encrypt and am getting an error, "couldnt communicate with key ring deamon"

How do I fix that?

---

### Post by kerry_s on 2010-05-28
check system-> startup applications
make sure its set to run.

for now you can open the file manager, press "ctrl+h" to show hidden, go to
.gnome2, delete "keyrings". you'll have to set it up again, this time leave it blank.

log out & back in

---

### Post by Jon_ on 2010-05-28
Ok, I got the password and encry thing to work. What keyring do I need to add exactly?

---

### Post by kerry_s on 2010-05-28
> **Jon_ said:**
> Ok, I got the password and encry thing to work. What keyring do I need to add exactly?

none, when you put the network password, it will ask you to set a password for the key manager, just leave that blank, then you won't have to unlock to connect.

---

### Post by Jon_ on 2010-05-28
Thanks, I finally got it. I deleted my old wireless connection and created a new one. This time I did what you said and left the password thing blank and rebooted the computer......guess what......it connected on it's own!!!!!

Thanks again for all your help everyone!

---

### Post by b k on 2010-05-28
> **Jon_ said:**
> Thanks, I finally got it. I deleted my old wireless connection and created a new one. This time I did what you said and left the password thing blank and rebooted the computer......guess what......it connected on it's own!!!!!
 
Thanks again for all your help everyone!
 
Just wanted to know if auto login into your _user account_ at computer boot up was one of the factors that contributed to your original problem.
 
Thanks

---

### Post by Jon_ on 2010-05-28
No, it was not, I am still able to do auto login and as it's loading the desktop it's connecting at the same time.......works great now.

---

### Post by kerry_s on 2010-05-28
thats great, i knew you would get it eventually. i have mine setup the same way, so i know it works, mine connects before even reaching the desktop.

---

