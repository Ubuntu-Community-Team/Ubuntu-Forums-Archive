---
title: "Controlling XMMS2 from a Webpage."
date: 2008-08-08
forum: Multimedia Software
---

### Post by The Altruist on 2008-08-08
I can't seem to get my xmms2 daemon to play songs as the www-data user so I can control my xmms2 from a web page via Apache2 w/PHP.

Things I've done.
[LIST]
[*]Made the www-data user part of the audio group.
[*]CHOWN'ed the music files to www-data.
[*]Created .config/xmms2 and .cache/xmms2 directories inside the web root.
[*]SUDO SU'ed into root, then "sudo -u www-data xmms2 play"
[/LIST]

I'm staring at this:
ERROR: Couldn't start playback: Could not start playback

What am I doing wrong? Granted, I'm a Linux noob, so this as far as I could think to do. I'm not very familiar with the audio systems or devices or such.

---

### Post by The Altruist on 2008-08-09
Sorry for the double post, but this one's falling off the radar. I      people who bump for the sake of bumping, but I do need help.

In a previous post long past, a user named Metz mentioned he created a file called .asoundrc. I'm wondering if I need such a thing, but it seems he only needed it for his second sound device, and I probably need to look elsewhere.

Any help would be greatly appreciated. Still getting an error: 
ERROR: Couldn't start playback: Could not start playback

---

### Post by stick_figure on 2008-09-05
We're having the same problem as well.  We're controlling xmms2 from a Django app.  I get the previously mentioned message when I execute 'xmms2 play' from the command line.  I may not have sufficient privileges, though, so I bet that's the problem.

---

### Post by Metz on 2008-09-12
Sorry for the late reply... don't get much time to myself at the moment :) I'll go back through the work I did at home tonight and try to provide a sensible answer later.

---

### Post by Metz on 2008-09-15
hmmm... right, it's been a while since I've done anything on this, but, this is the setup I'm currently running which seems to work....

a) .asoundrc file configured in the document root.
b) xmms is installed in the document root. Not sure if that's actually needed, but that where it is now, and it works.I know this is slightly vague and shoddy...but as I said, it's been a year since i did any work on this, and it works, so I ain't fixing it right now ;)
c) The front end is written in php, for the most part...with an iframe receiving signals via javascript to make 'exec' calls for the various facitilies.. list this :-

```

function action_play() {
	$retval = exec('xmms2 play', $results);
	redirect();
}

```


So, the only additional info I've been able to add is that .xmms is present in /var/www, and www-data has permissions to all this.

---

