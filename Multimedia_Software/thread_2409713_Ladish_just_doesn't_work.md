---
title: "Ladish just doesn't work"
date: 2019-01-05
forum: Multimedia Software
---

### Post by chippyash-2 on 2019-01-05
Ubuntu Studio 18.10

I am just about to throw in the towel on using Ubuntu Studio for audio production.  The parts work. Ardour 5.x great; Hydrogen, Yoshimi lovely.  All in and of their own right.  But trying to put put together a studio using (g)ladish just doesn't work.

It's a real problem. I don't have a particularly complex set-up.  Some analogue in via a Scarlet 2i2, midi controller via m-audio oxygen-61. I use Ardour, Yoshimi and Hydrogen on t'pooter.  

BUT getting it all to work together consistently is a royal PITA.

I see that [http://ladish.org/](http://ladish.org/) suggest that the project is either a/ no longer supported or b/ no one gives a damn.

Ok, so to a solution. I'm not a C programmer.  Do I need to be in order to work with JACK?  I do PHP and Python. Can I get at JACK with either of those?  (well, I know I can as an exec cmd but others may have short-cuts)

Outline requirement:
 - fire up 'app'
 - it loads all applications required
 - it then loads JACK (or does this need to be before previous step?)
 - it makes 'saved' connections between each application

It's kinda what ladish should be doing but isn't.

Not asking for anyone to provide it.  But if you have knowledge on how to do it, then I can at least start the process of programming it

---

