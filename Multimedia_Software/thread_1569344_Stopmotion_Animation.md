---
title: "Stopmotion Animation"
date: 2010-09-06
forum: Multimedia Software
---

### Post by isaacahloe on 2010-09-06
Hi, Linux does not have an active stop motion program. Stopmotion ([http://developer.skolelinux.no/info/stu … topmotion/]("http://developer.skolelinux.no/info/studentgrupper/2005-hig-stopmotion/") ) is awesome, but is inactive for feature developement.

here is an idea in a letter that I sent to the developers of stop motion involving the use of gphoto as an addition backend for still cameras. below the letter is their very supportive response:

"Hi. I assume you all aren't actively working on stop motion anymore, but I
think if you were to pick it up again, integrating with gphoto would be an
awesome feature. You might look at how Digikam retrieves photos using it as
i know it can utilize it. This would allow people with still cameras,
especially newer dslrs (i have a Nikon D90), to get really high quality
results. it would really put the program in a different league. It already
supports dv cameras, but if it had support for still cameras, even dslrs, it
would replace many people's need for another stop motion program.

I know it could be done pretty easily too, but i know nothing about coding a
program.

in Stopmotion, if I put "gphoto2 camera-capture" as the startup daemon, it
causes my camera to take a picture when i hit the button to connect the
program to the camera.

The connection button could be set to configure gphoto to transfer pictures
straight to the computer instead of to the ram or to memory card on the
camera. Then hitting the capture button would just capture the frame.

tell me what you think. If you think it's a good idea, perhaps i can search
the kdenlive or Digikam forums or something for someone who can help
implement this if you would not be able."

REPLY FROM A DEVELOPER

"Hi Ike,

Sorry for the late answer.

I  think it sounds like a great idea! No such software existed when we (at  least I) where last actively developing stopmotion. However, I don't  have time to work on stopmotion these days and I believe Bjorn only has  time for maintenance, not implementing new features.

If anyone else would be interested in developing it then I think that is a great idea as well.

best,
Fredrik Kjolstad"

The two main points I think need to be developed to put this program to a professional level are

1. integration with gphoto or a good backend for capture images from still cameras
2. enhance the settings and configuration gui to make it easy to set up your camera, project size, import/export settings, etc.
3. (very wishful) merge Stopmotion and Pencil to create one frame based, onion skinning, ultimate animator fun house.

I  figure Digikam, Pencil, and Kdenlive developers would be the best to  ask. Digikam poeple already know how to hook up to gphoto so that should  be super easy. Kdenlive and Digikam poeple know about configuration and  project management. Kdenlive could actually start forming a small suite  for time media editing.

and to my last idea: merge Pencil's progress and Stopmotion into one effort.

Pencil's  code/features could be merged with Stopmotion, or most probably the  other way around. Pencil could use Stop Motion's code to create a "stop  motion" layer like they have camera, vector, bitmap layers. The capture  module could select which stop motion layer to send the image. They both  are a solution for similar things. They both handle frame based  animation/film and they both require onion skinning and other features.  Merging them would allow rotoscoping and animation over film. If a  chroma key effect was present I can't even imagine the full  possibilities.

This would also be good because while pencil is actively developed (although th edev seems very busy), pencil is developed for mac mainly, so the linux side of things is not given the same weight. A project like this could put full emphasis on the linux side of things.

All of these technologies are currently being used  in Qt/KDE applications already... It seems like coding (i know nothing  by the way) would be more a matter of linking up already written code  and writing new code to smooth it out.

So you see I'm looking to  see how I could go about getting something started. I know nothing about  code. And the developers are not able to work on this. But i'm willing  to do what I can and when I can.

if anyone knows how i can edit  this post to be more concise and effective let me know. I want this to  be read and thought about, but I also want all of the ideas present.

---

### Post by Yellow Pasque on 2010-09-06
You might want to post something on the digikam developers' mailing list: [http://www.digikam.org/drupal/support](http://www.digikam.org/drupal/support)
Good luck.

---

### Post by super.niels on 2010-11-25
it sounds like a great idea, i have my self just discovered that gphoto2 can capture pictures, and have been doing a couple of time-lapse movies. My next step was to combine time-lapse and stop-motion, so keep up the good work!

---

