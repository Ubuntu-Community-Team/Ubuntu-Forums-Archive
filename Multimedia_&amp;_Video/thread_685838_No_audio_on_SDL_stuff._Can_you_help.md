---
title: "No audio on SDL stuff. Can you help?"
date: 2008-02-02
forum: Multimedia &amp; Video
---

### Post by BigSilly on 2008-02-02
I don't know why this has suddenly started happening, but not long ago these programs were running fine. Now suddenly I get this error when I try to run Secret Maryo Chronicles and sdlmame and others from a terminal:

```
Last known SDL Error : No available audio device
```

Anyone here who can help me fix this? As I say up till recently these ran fine. I can't imagine what I've done to cause this problem.

Many thanks in advance.

EDIT: OK, I've installed libsdl1.2debian-all from the repository, which seems to offer the sdl sound support needed. Thankfully it's given me the audio I should have, but now I get this error when running smc (Secret Maryo) from the terminal:

```
Last known SDL Error : Failed loading DPMSDisable: /usr/lib/libX11.so.6: undefined symbol: DPMSDisable
```

Can you help with this? Sorry to be a pain...

---

