---
title: "Volume Control no longer has any effect on mic volume"
date: 2008-01-25
forum: Multimedia &amp; Video
---

### Post by accatagon on 2008-01-25
I made the mistake of attempting to use Ekiga. I already had an account, so I set everything up, and it was all working except for one small glitch. When I closed it, it did not stop receiving input from the microphone. It still echoed back my voice despite the fact that the microphone was turned off in the Gnome volume control. 

I decided to see what would happen if I restarted my computer. Big mistake. . .
It could not detect the Gnome settings daemon. I ended up fixing the problem by uninstalling Ekiga.

Unfortunately, the volume control for my microphone is still in the unreachable netherworld. Do have to put up with the slight fuzziness inherent in sending a mic signal to the speakers forever (or until reinstalling Ubuntu or another distro?), or is there some way to get control for the microphone volume back in the hands of the volume control applet.

Also, Ekiga really should work without blowing up everything. If it really normally crashes everything like it did on my computer, then it seems to imply that the software is completely defective and actually harmful to even try. 

Thanks for letting me rant. . . seriously, is there any way to recover volume control to my mic? I have some form of creative labs SBLive! sound card, a pentium 4 processor, Gutsy Gibbon, compiz enabled, and an nvida geforce 4 MX420.

Edit: 
So. . . it turned out the input was coming from some AC97 channel. Ubuntu/Gnome/Linux someone really needs to clean up the audio mess in Linux. I shouldn't need to have to track down the channel that is getting input, it should all be controlled by the microphone channel. I know that was one of the improvements slated for a future version of Ubuntu, so kudos to whoever picks it up, if anyone does. Anyway, I think the weirdness with Ekiga has to do with my computer just acting generally bizarrely, despite always passing memory tests and filesystem checks. Sorry to bother.

---

