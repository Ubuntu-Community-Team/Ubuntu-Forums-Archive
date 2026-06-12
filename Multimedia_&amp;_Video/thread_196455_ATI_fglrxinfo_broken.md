---
title: "ATI fglrxinfo broken"
date: 2006-06-14
forum: Multimedia &amp; Video
---

### Post by dominikroblek on 2006-06-14
I installed proprietary 'fglrx' ATI driver on my Ubuntu Dapper following the rules on [BinaryDriverHowto/ATI]("https://wiki.ubuntu.com/BinaryDriverHowto/ATI"). After some manual changes to xorg.conf everything appears to work fine.

However, if I execute the 'fglrxinfo' command I get the following output (I included only a part of it, since it is very long):
...
[fglrx] API ERROR: could not register entrypoint for ProgramEnvParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4fvARB
[fglrx] API ERROR: could not register entrypoint for ProgramLocalParameter4dvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramEnvParameterdvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterfvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramLocalParameterdvARB
[fglrx] API ERROR: could not register entrypoint for GetProgramivARB
[fglrx] API ERROR: could not register entrypoint for GetProgramStringARB
[fglrx] API ERROR: could not register entrypoint for GetVertexAttribdvARB
...

Do you have any idea, what is wrong?

I attached my xorg.conf.

Thanks in advance,
Dominik

---

### Post by danoyoto on 2006-06-14
look [here]("http://ubuntuforums.org/showthread.php?t=185033")

---

### Post by dominikroblek on 2006-06-14
[QUOTE=danoyoto]look [here]("http://ubuntuforums.org/showthread.php?t=185033")[/QUOTE]

Thanks, it solved my problem!

---

