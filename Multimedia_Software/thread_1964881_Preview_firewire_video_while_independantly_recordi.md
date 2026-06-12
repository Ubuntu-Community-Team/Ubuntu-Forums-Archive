---
title: "Preview firewire video while independantly recording/enccoding"
date: 2012-04-24
forum: Multimedia Software
---

### Post by tartan75 on 2012-04-24
I’m looking to take a firewire video feed (which I’m  initially grabing with dvgrab), and pipe it to:
 1)      1) Preview window  permanently
 2)      2) When at the right point while previewing, start dvgrab (or i suppose ffmpeg) to record an avi and  ffmpeg to encode it to mpeg ready for dvd production.
  
 I can do this with a tee pipe no problem except that I must  start all at the same time or the pipe blocks. Any suggestions would be great.  I’ve tried:
 1)      a) dvgrab interactive mode, but  this doesn’t seam to work when stdin is the input to the interactive instance of  dvgrab
 2)      b) Looking into  non-blocking pipes, or multitee as an option. Didnt get on well with Multitee,  but found little to guide me. I wasn’t seeing an obvious working solution for  either of these.
 3)      c) Video loopback driver.  The only one I found was V4L, and from [http://www.kinodv.org/dcforum?az=show_topic&forum=102&topic_id=908](http://www.kinodv.org/dcforum?az=show_topic&forum=102&topic_id=908)  it doesn’t appear an ideal solution anyway.
  
 I struggle to believe what I’m trying to do is that unusual,  so am I missing an obvious solution, or can anyone suggest a direction I should  look in?
  
 Any advice much appreciated.
  Nathan

---

