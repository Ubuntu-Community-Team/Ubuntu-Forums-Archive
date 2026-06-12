---
title: "sipie factory autherror"
date: 2008-09-26
forum: Multimedia Software
---

### Post by myname on 2008-09-26
Hello all,

I came in to work this morning, fired up the computer, and launched sipie, like I do every morning.  However, this AM, I was greeting to the following:

```

./sipie.py
Traceback (most recent call last):
  File "./sipie.py", line 22, in <module>
    Sipie.cliPlayer()
  File "/home/kpodbielniak/Download/Sipie-0.1196144357/Sipie/cliPlayer.py", line 74, in cliPlayer
    completer = Completer(sipie.getStreams())
  File "/home/kpodbielniak/Download/Sipie-0.1196144357/Sipie/Factory.py", line 377, in getStreams
    streams = self.tryGetStreams()
  File "/home/kpodbielniak/Download/Sipie-0.1196144357/Sipie/Factory.py", line 308, in tryGetStreams
    raise AuthError
Sipie.Factory.AuthError

```

Any idea?  as my day in this small dark room will be very LONG without my sirius radio.  :(

--k

---

### Post by myname on 2008-09-26
this has been fixed.  I deleted everything in the ~/.sipie directory and relaunched sipie, and it's working.

--k

---

### Post by llamakc on 2008-09-26
Did you reinstall? Clearing out my ~/.sipie and reentering the credentials still resulted in:

```

Traceback (most recent call last):
  File "/usr/bin/sipie.py", line 5, in <module>
    pkg_resources.run_script('Sipie==0.1196144357', 'sipie.py')
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 448, in run_script
    self.require(requires)[0].run_script(script_name, ns)
  File "/usr/lib/python2.5/site-packages/pkg_resources.py", line 1173, in run_script
    exec script_code in namespace, namespace
  File "/usr/bin/sipie.py", line 22, in <module>
    
  File "build/bdist.linux-i686/egg/Sipie/cliPlayer.py", line 74, in cliPlayer
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 377, in getStreams
  File "build/bdist.linux-i686/egg/Sipie/Factory.py", line 308, in tryGetStreams
Sipie.Factory.AuthError

```

---

### Post by myname on 2008-09-26
Nope, I just cleared it out and re ran ./sipie.py.

Though the stream was cutting in and out, I had to keep pressing Play to restart the stream.  Not sure if it's related to sipie, or if sirius was just having a crappy day streaming.

--k

---

### Post by llamabr on 2008-09-26
rm'ing my ~/.sipie also worked for me.  I've only done it a minute ago, and havn't checked if it's going to cut in and out.

But I'm sure glad I don't have to go through that egg business again.

---

