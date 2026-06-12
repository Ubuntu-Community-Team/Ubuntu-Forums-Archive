---
title: "Problem with LiveTV and two Nova-S cards in MB 8.10 x64 backend"
date: 2009-09-30
forum: Mythbuntu
---

### Post by nzsouthernman on 2009-09-30
I've just added a second Hauppauge Nova-S DVB-S card to my backend (8.10 x64).

I have multirecord set up (3 tuners per card) and have am watching two satellite transponders here in NZ for Freeview.

Both DVB0 and DVB1 share the same Video Source, called 'Manual'.

I'm able to record off both transponders at the same time no problem, and can multirecord off them both as well.

However, when I watch LiveTV I can select any channel across both transponders from one frontend, but if I start LiveTV from another frontend I cannot select a channel from a different transponder than the one the first frontend is locked in to. (ie won't use the second Nova-S card). What do I need to do to allow a second instance of LiveTV to invoke the second Nova-S card if required?

My second problem is probably related - if we're watching LiveTV off one transponder (say TV2 for example) and a scheduled recording kicks in for TV3 (different transponder) we get booted out of TV2 and dropped into TV3 for LiveTV and then can only select channels from the TV3 transponder. Exiting LiveTV and coming back in and we can still only select channels from the transponder that TV3 is recording from. This looks like the scheduler is using DVB0 by default for the first recording & LiveTV only.

Anyway, if anyone is able to shed any light on this for me I'd really like to be able to watch LiveTV and not have Myth kick us out of it when a recording kicks in.

Cheers

---

