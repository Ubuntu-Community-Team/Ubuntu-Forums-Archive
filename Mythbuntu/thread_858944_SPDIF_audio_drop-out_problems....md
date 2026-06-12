---
title: "SPDIF audio drop-out problems..."
date: 2008-07-14
forum: Mythbuntu
---

### Post by jimsiff on 2008-07-14
I'm having problems with my SPDIF connection to my receiver. When I watch DVDs, archived videos, and rarely Live and Recorded TV in Myth, I get a lot of random audio drop outs. I can see my receiver switching from DD5.1 to DPLII if the signal drops for longer than a few seconds.

I'm running Mythbuntu 8.04. I'm using a Biostar TN720 mobo w/ AMD 5000+, a SPDIF header adapter mounted to an expansion slot cover, and a Blue Jeans Cable 6' 75 ohm coax digital audio cable connected to a Pioneer VSX-54TX receiver. I don't think the SPDIF connection is bad, because if I swtich xine to use stereo over SPDIF instead of AC3 DD5.1, audio is clean.

Any help, tips, or troubleshooting rsources would be greatly appreciated. This is driving me nuts, and I won't cancel DirecTV until the audio glitches are cleaned up.

Thanks,

Jim

---

### Post by foxbuntu on 2008-07-14
I would suggest switch to SPDIF passthrough rather than letting myth handle it based on your information. 

Utils/Setup > Setup > General > 3rd page (IIRC) Enable SPDIF Passthrough

---

### Post by jimsiff on 2008-07-14
> **foxbuntu said:**
> I would suggest switch to SPDIF passthrough rather than letting myth handle it based on your information. 

Utils/Setup > Setup > General > 3rd page (IIRC) Enable SPDIF Passthrough

Thanks for the reply.  My original post wasn't completely clear.  I believe I am using SPDIF passthrough.  SPDIF coax to my receiver is the only audio connection on my HTPC.  SPDIF passthrough is enabled in Myth general setup.  The audio output device is set to "ALSA:plughw:0,1" which I believe correlates to my SPDIF output.

---

### Post by ndeubert on 2008-10-14
Hey Jim.
Did you ever find a solution to this problem? I've tried the coax SPDIF on 2 different sound cards(sb live 5.1 PCI and CMedia CMI8738) and 2 different digital receivers and I still got frequent drop outs and it's driving me nuts! I even just upgraded to Intrepid to see if that mattered, but now i'm thinking it must be some kind of noise/buffering issue with alsa because i get it even with aplay.
Thanks,
Nick

---

