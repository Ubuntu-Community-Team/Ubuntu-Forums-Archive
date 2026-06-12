---
title: "Using a Mac? Eliminate that blue tint!"
date: 2009-03-26
forum: Multimedia Software
---

### Post by Peasantoid on 2009-03-26
If you're running Ubuntu on your Mac, you may have noticed that your screen has this irritating blue tint. The instructions located in the Mactel installation guide [here](https://help.ubuntu.com/community/MacBook2-1/Hardy#Screen%20Colors%20(optional)) can fix that for you, but certain 3D applications (games for instance) still cause it to come back. I kludged my way around it with this shell script:
```
#!/bin/bash
while [ 1 ]; do
	xcalib /usr/local/etc/OSX_Colors.icc # Or wherever your .icc file is located.
	sleep 10 # Wait ten seconds, then repeat the loop.
done
```
This is essentially an infinite loop. It calibrates the monitor, waits ten seconds, and repeats. There are probably much cleverer ways of doing this, but I have yet to find them.

Set it to run at login (System > Preferences > Sessions) and you should be all set.

Tested with the Quake3-based games Warsow and Nexuiz.

[ EDIT ]

Here is a much less kludgy solution. It involves creating two scripts: a "wrapper" to run a certain program and one similar to the above "infinite-loop" code.

Code for the wrapper (in this case, xcalib-wrapper.sh):
```
#!/bin/bash
/path/to/xcalib-loop.sh & # Run the infinite-loop file as a background process.
xspid=$! # $! means the PID of the last command.
$1 # Launch the command specified by argument 1. When it's done...
kill $xspid # ...kill the xcalib script.
```
To run Warsow, for example, do this: xcalib-wrapper.sh warsow

Code for xcalib-loop.sh:
```
#!/bin/bash
while [ 1 ]; do
	xcalib /usr/local/etc/OSX_Colors.icc # Or wherever your .icc file is located.
	sleep 10 # Wait ten seconds, then repeat the loop.
done
```
The idea of this solution is that you're only running the xcalib loop while the game is actually being played, so you don't waste precious system resources on calibrating the monitor for no reason.

---

### Post by Peasantoid on 2009-03-31
I created a less kludgy solution. See original post.

---

