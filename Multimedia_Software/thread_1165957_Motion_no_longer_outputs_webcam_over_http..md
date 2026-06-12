---
title: "Motion no longer outputs webcam over http."
date: 2009-05-21
forum: Multimedia Software
---

### Post by dchurch24 on 2009-05-21
Hi all,

I have several machines in my house, and so I thought it would be a good idea to use them with cheap webcams to monitor any motion in the place when I was out.

However, one has simply stopped working.

I start motion from the terminal, and sometimes is says that it is starting a stream on port 8081 and other times is stops at "[1] Using V4L1".

In both instances if I try to connect either through VLC or Firefox on port 8081 I get nothing.

At one point it DID give me a quick snapshot that was half rubbish and half a snap of my living room - but it only did that as I killed the process.

Nothing on this machine has changed - not even an update since the last time it was working.

motion.conf (webcam server bit)

```


############################################################
# Live Webcam Server
############################################################

# The mini-http server listens to this port for requests (default: 0 = disabled)
webcam_port 8081

# Quality of the jpeg images produced (default: 50)
webcam_quality 50

# Output frames at 1 fps when no motion is detected and increase to the
# rate given by webcam_maxrate when motion is detected (default: off)
webcam_motion on

# Maximum framerate for webcam streams (default: 1)
webcam_maxrate 5

# Restrict webcam connections to localhost only (default: on)
webcam_localhost off

# Limits the number of images per connection (default: 0 = unlimited)
# Number can be defined by multiplying actual webcam rate by desired number of seconds
# Actual webcam rate is the smallest of the numbers framerate and webcam_maxrate
webcam_limit 0

```

Please help, I am completely at a loss now.

---

