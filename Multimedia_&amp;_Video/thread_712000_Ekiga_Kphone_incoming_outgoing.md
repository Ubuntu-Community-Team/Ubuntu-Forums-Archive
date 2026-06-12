---
title: "Ekiga Kphone incoming outgoing"
date: 2008-03-01
forum: Multimedia &amp; Video
---

### Post by jARLAXL on 2008-03-01
struggling for quite some time now with softphones:

In brief: 
Ekiga will not be able to connect to an incoming call (though it pops up and opens the codecs) while Kphone responds to an outgoing call:call Failed unauthorized.](*,)

In detail:
Configuration:
System: Ubuntu Gutsy Gibbon. Firewall:Guarddog. NAT:yes! opened (forwared) ports 5000-5100 1720(also triggered) 8000 7078 3478 etc etc. VOIP provider: Betamax (voipdiscount). User:absolute noob.

Situation:
Ekiga:
I can make outgoing calls using ekiga normally since router configured to forward ports.
However eventhough i can see when i am being called (window pops up) when i accept the call neither me nor the caller hear anything. Disabling firewall and or running as DMZ 
does not change the situation. Occasionaly (once-today) i succeed on incoming calls but when i try to reproduce it, it doesnt succeed. Furthermore when i try to text chat i receive an unauthorized error. A minor problem is that the one being called suffers from echo effect.

Kphone: I can receive incoming calls normally but an outgoing call will respond call failed:unauthoried. Furthermore when firewall rules change i have to restart Kphone in order to receive incoming calls as a message about some other program using my soundcard appears(though i havent opened any such music player or whatever). Disabling guarddog firewall does not change the situation.

Any ideas on how i can solve the problem using any of these softphones (or even an alternative).
Thanks in advance.

---

### Post by jARLAXL on 2008-03-01
I believe the problem is related to what is referred to:
by kitsos as:[http://ubuntuforums.org/showthread.php?t=298700&highlight=kitsos]("http://ubuntuforums.org/showthread.php?t=298700&highlight=kitsos")
> Something interesting that i came accross somewhere is that if your router is VOIP enabled, it might be hijacking all SIP traffic and handling it by itself...if that is the case you need to disable VOIP in your router.

I say this cause i managed to run twinkle flawlessly but without firewall. Using firewall i couldnt isolate any ports, as when i added rules they worked only randomly.eg: if i  opened ports 1:30000 (30k) twinkle would accept incoming and or make outgoing calls successfully about 1/2 of the time. 

i will check with the router owner and be back in this thread.

**_UPDATE:_**finally i managed to make twinkle work under firewall. it seemed that a preset rule had to be enabled in guarddog firewall: Network information service NIS under Network protocols.

**UPDATE2:**: the one who receives my call is experiencing echo (twinkle). probably this is due to NAT issues as ekiga without NAT doesnt show the same behaviour.

---

