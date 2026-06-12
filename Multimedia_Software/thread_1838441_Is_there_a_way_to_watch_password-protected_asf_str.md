---
title: "Is there a way to watch password-protected asf stream?"
date: 2011-09-03
forum: Multimedia Software
---

### Post by azangru on 2011-09-03
There is an asf video stream I'd like to watch, but the access to it requires username and password. On a Windows machine (not mine) I can enter the address of the stream in Windows Media Player, and it produces an interface dialog, where I can enter the username and the password. On my Linux machine, however, I can't find a single video player that is capable of offering this interface dialog. I tried VLC, but got the following error:

```
Your input can't be opened:
VLC is unable to open the MRL <file name>. Check the log for details.
```

And the Messages box informs that:

```
main info: stopping playback
access_mms error: error: HTTP/1.0 401 Unauthorized
main error: open of <file name> failed: (null)
```

I also tried to modify the stream address to include both the username and password in it:

[http://my-login:my-password@wms.the_rest_of_address](http://my-login:my-password@wms.the_rest_of_address)

That didn't help.

I tried Mplayer (with KMplayer frontend) - nothing.

So, is it possible to play password-protected stream video on a Linux machine?

*(Just in case, I use OpenSUSE 11.4 with KDE, but I hope that's not terribly important)*

---

### Post by andrew.46 on 2011-09-03
MPlayer is able to add in username and password by using the *-user [COLOR="Red"]<username>[/COLOR]* and *-passwd [COLOR="Red"]<password>[/COLOR]* options although I will admit I have never actually used these options with MPlayer :).

---

### Post by azangru on 2011-09-03
> **andrew.46 said:**
> MPlayer is able to add in username and password by using the *-user [COLOR="Red"]<username>[/COLOR]* and *-passwd [COLOR="Red"]<password>[/COLOR]* options although I will admit I have never actually used these options with MPlayer :).

How to you use these options? Only through the console? Do I enter the command that looks like this:

mplayer -user username -passwd password actual_url?

Update: Tried this command, but it didn't work. What I received was this error:

Resolving <url> for AF_INET6...
Couldn't resolve name for AF_INET6: <url>

:-(

---

### Post by andrew.46 on 2011-09-03
> **azangru said:**
>  Do I enter the command that looks like this:

```
mplayer -user username -passwd password actual_url?
```

Update: Tried this command, but it didn't work. 

Certainly that is how I would use the commandline myself, if this does not work I am afraid that I have no other solutions :(. Hopefully somebody else on these forums can help out...

---

### Post by Aster.Orthrinos on 2011-10-12
I also need some software to play protected asf stream, VLC and MPlayer cannot do this, maybe somebody could suggest something else?

---

### Post by Xelort on 2011-10-12
"HTTP/1.0 401 Unauthorized"...

hmmm...

What do you see when you enter the url in a web browser? It should ask you for username and password if that's actually the problem and we're talking about HTTP. Maybe you can just download it that way an play it later...

---

### Post by andrew.46 on 2011-10-12
> **Aster.Orthrinos said:**
> I also need some software to play protected asf stream, VLC and MPlayer cannot do this, maybe somebody could suggest something else?

Always a little difficult to diagnose the problem without looking at the stream itself. Can you give details of the stream? If username and password cannot be shown on the Forums feel free to PM me the details if that is appropriate...

---

