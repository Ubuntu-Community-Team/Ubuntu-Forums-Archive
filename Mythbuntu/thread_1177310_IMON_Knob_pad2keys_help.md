---
title: "IMON Knob pad2keys help"
date: 2009-06-03
forum: Mythbuntu
---

### Post by ddoctor on 2009-06-03
Hi,

I want to use the touch-sensitive pad controller on my IMON remote as keyboard navigation. It's an "IMON Knob" - a volume knob/IR receiver + IMON PAD.

There's supposed to be a pad2keys patch that's included in Mythbuntu 9.04, which translates strings of "mousey" commands to distinct Up/Down/Left/Right. I can't get it to work.

lircd.conf.imon-knob has CursorUp etc bindings e.g.
CursorDown               0x6882A1B7

I added them to my mythtv lircrc thingy:
begin
    remote = IMON_KNOB
    prog = mythtv
    button = CursorDown
    config = Down
    repeat = 0
    delay = 0
end


It seems to work at a very light pressure. Press harder - nothing. It's kinda useless.

Running mode2 gives me different codes for different pressures. Now, the pad2keys patch is supposed to stop that, right? It should translate a string of different pressure codes to the single code, to be interpreted as a key press.

I get the feeling that the pad2keys patch is for different IMON PAD products, and doesn't work for the IMON Knob.

It seems like the only option I have is to add bindings for each pressure value, which would be difficult and error-prone.

Does anyone else have this problem? Any solutions? Thanks.

---

