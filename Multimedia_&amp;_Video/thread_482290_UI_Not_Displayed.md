---
title: "UI Not Displayed"
date: 2007-06-23
forum: Multimedia &amp; Video
---

### Post by reimmer on 2007-06-23
Hi guys,
    I saw a Ubuntu CD today. It was very impressive(n I hate Microsoft) so I installed it. The Live CD works perfectly OK but in the installed version, the UI doesn't show up. I get till the login screen. I can enter my username and password, but then all I get is a brown screen without the desktop or buttons.

I have an Intel 945GM Graphics card, Intel Core2 Duo 1.73 Ghz Processor.


Please do help me.

Thanks

---

### Post by taurus on 2007-06-23
What happens if you run this command from a prompt after you log in?

```
startx
```

---

### Post by reimmer on 2007-06-23
The command prompt works fine..only the Graphical mode doesn't work..

---

### Post by Rui Pais on 2007-06-23
Hi,
what happens when you run:
```
sudo /etc/init.d/gdm restart
```
did it starts or output any errors?

---

### Post by reimmer on 2007-06-23
Display Manager restarts, asks for my username and password but then it's the same story-same brown screen with no buttons...but my LiveCD works properly..

---

### Post by Rui Pais on 2007-06-23
Can you post the output of
```
cat .xsession-errors
```
after you get one of the brown screens?

And do you tried taurus suggestion (but closing gdm first)?
```
sudo /etc/init.d/gdm stop
startx
```
Did it work then?

---

### Post by reimmer on 2007-06-24
> Can you post the output of
Code:

cat .xsession-errors



It just has normal display log messages. No errors of any sort.
> 
And do you tried taurus suggestion (but closing gdm first)?
Code:

sudo /etc/init.d/gdm stop
startx

Did it work then?

If I stop it n then start it, the screen becomes corrupt n there are a lot of error messages in the command-prompt Terminal (1)

---

### Post by Ziox on 2007-06-24
to have a complete look at X, you can look at its log, though I'm not sure if it'll tell us much.

Here's the code:

cat /var/log/Xorg.0.log

or

cat /var/log/Xorg.0.log.old

they both are extremely long files, so I would suggest posting its entirety with the code command.

---

