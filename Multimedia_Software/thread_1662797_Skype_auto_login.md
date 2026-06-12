---
title: "Skype auto login"
date: 2011-01-08
forum: Multimedia Software
---

### Post by Robbyx on 2011-01-08
I am having to use a bash script to login to skype. Does anyone know the syntax of the command line so that I do not have to keep entering the password when starting skype? I have tried various different formats.

> #!/bin/bash
export XLIB_SKIP_ARGB_VISUALS=1
export LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so
# echo user1 password1 | /usr/bin/skype  --pipelogin
# the above does not keep the login on the screen and the login does not proceed.
/usr/bin/skype 
# this works but does not recall the password.


---

### Post by ajgreeny on 2011-01-08
Why should you need to use a bash script?

Is it to get the webcam to work in skype?

I did have that problem at one time but the shell script to which I pointed in the startup applications was simpler than yours and did not need a password.
```
#!/bin/bash
export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
skype
```

---

### Post by Robbyx on 2011-01-08
> **ajgreeny said:**
> Why should you need to use a bash script?

Is it to get the webcam to work in skype?

I did have that problem at one time but the shell script to which I pointed in the startup applications was simpler than yours and did not need a password.
```
#!/bin/bash
export LD_PRELOAD=/usr/lib/libv4l/v4l2convert.so
skype
```

As a result of a fresh install I have been having a lot of problems getting the video to work in skype. I have tried your script and thank you for it, especially as I have been able to add in the command to enter the skype login password to the script.

Robin

---

### Post by ottabaub on 2011-01-27
> **Robbyx said:**
> As a result of a fresh install I have been having a lot of problems getting the video to work in skype. I have tried your script and thank you for it, especially as I have been able to add in the command to enter the skype login password to the script.

Robin

Would you mind posting your script so I can duplicate what you've done? My webcam works just great but it's such a nuisance to have to type my password in every time I boot.

---

### Post by towheedm on 2011-01-27
Why not just check 'Sign me in when Skype starts'?

---

### Post by ottabaub on 2011-01-27
> **towheedm said:**
> Why not just check 'Sign me in when Skype starts'?

I know. Sounds simple doesn't it? But it only remembers my login name. I have to type in the password every time.

---

### Post by towheedm on 2011-01-27
It remembers my password, even if I logout or reboot.  I have noticed though, if I Sign Out before closing Skype, it asks for the password the next time I start Skype.

Now I have an EyeToy cam and this is what I did:

1.  Rename [COLOR=Blue]/usr/bin/skype[/COLOR] to[COLOR=Blue] /usr/bin/skype.rea[/COLOR]l
```
sudo mv /usr/bin/skype /usr/bin/skype.real
```2.  Create a new file named [COLOR=Blue]/usr/bin/skype[/COLOR] and paste the following 2 lines into it:
```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so XLIB_SKIP_ARGB_VISUALS=1 skype.real
```3. Make it executable:
```
sudo chmod +x /usr/bin/skype
```

---

### Post by ottabaub on 2011-01-27
> **towheedm said:**
> It remembers my password, even if I logout or reboot.  I have noticed though, if I Sign Out before closing Skype, it asks for the password the next time I start Skype.

Now I have an EyeToy cam and this is what I did:

1.  Rename [COLOR=Blue]/usr/bin/skype[/COLOR] to[COLOR=Blue] /usr/bin/skype.rea[/COLOR]l
```
sudo mv /usr/bin/skype /usr/bin/skype.real
```2.  Create a new file named [COLOR=Blue]/usr/bin/skype[/COLOR] and paste the following 2 lines into it:
```
#!/bin/bash
LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so XLIB_SKIP_ARGB_VISUALS=1 skype.real
```3. Make it executable:
```
sudo chmod +x /usr/bin/skype
```

That sounds interesting. I don't have an EyeToy cam, though. Just the one built into my ASUS netbook. Nevertheless I'll try your method and see what happens. Thanks.

---

### Post by ottabaub on 2011-01-28
I figured out what I needed to do and now it seems to be working fine. I typed up the procedure.

If Skype keeps asking for the password;
	- close Skype
	- open /home/<user>/.Skype/<user_folder>/
	- delete the file profile###.dbb
	- restart Skype
	- type in password
	- click to save password
	- click login button

Skype should start and log you in directly thereafter.

---

### Post by warfie on 2011-08-01
I'm interested in this too... I have multiple Skype accounts, I have them running all the time, I'd like it if I could have them start and login automatically when I login to Ubuntu.

---

