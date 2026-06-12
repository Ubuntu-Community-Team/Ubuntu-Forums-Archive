---
title: "Launching mplayer through ssh"
date: 2009-12-03
forum: Multimedia Software
---

### Post by jney on 2009-12-03
Hello,

  I got 1 pc and 1 laptop.
i would like to launch mplayer on the pc with my laptop connecting in ssh. and control mplayer.

Is it possible ?

---

### Post by Lars Noodén on 2009-12-04
Yes, you can:

```

ssh -X -l jney  pc
mplayer /path/to/movie.mov

```

or

```

ssh -X -l jney  pc  "mplayer /path/to/movie.mov"

```

---

### Post by jney on 2009-12-06
hhmmm... actually i knew how worked ssh. 

what i want to do is to launch a movie with mplayer on remote pc and be able to watch it on that remote pc.

---

### Post by Lars Noodén on 2009-12-07
> **jney said:**
> 
what i want to do is to launch a movie with mplayer on remote pc and be able to watch it on that remote pc.

Ok.  (BTW I fixed a typo above.)

You'll want to know what display to target.  Usually it is :0.0 and it is set in the environment variable "Display".  'export' passes the value available to programs launched from that shell.  The part before the colon is where a machine name could go, but that's left blank to mean local host, which if you are logged into the remote host is the remote host. ;)  

```

$ ssh -l jney  pc
export DISPLAY=**:0.0**
mplayer /path/to/movie.mov

```

There's not any good basic intro to [X](http://linux.die.net/man/7/x) that I know of, but some info can be found in the Display Names section of the X manual.  You can use the 'geometry' settings to place the new program in a particular area on the screen.

```

$ ssh -l jney  pc
export DISPLAY=**:0.0**
mplayer -geometry 400x300-1-1 /path/to/movie.mov

```

If you are using a key to connect to the remote machine, then you can pass the value of DISPLAY with the key itself.  The section on the authorized_keys file format in [sshd](http://linux.die.net/man/8/sshd) goes into a bit of detail.  The server will have to allow PermitUserEnvironment for that user's group.

---

### Post by jney on 2009-12-07
Thank you Lars !** "export DISPLAY=:0.0" **is what i was looking for.

i updated my zshrc to know if i'm connecting my terminal through ssh like it :

<pre>
if [ -n "$SSH_TTY" ]; then
  export DISPLAY=:0.0
fi
</pre>

---

