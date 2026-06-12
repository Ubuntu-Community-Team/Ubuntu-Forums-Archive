---
title: "Sounds drivers/ headphones"
date: 2011-07-22
forum: Multimedia Software
---

### Post by Number1luda on 2011-07-22
Right, I am having some sounds problems, when I connect my headphones to my laptop (Asus P50IJ) I cant disable the speakers, having sounds from both in this case. Or not having sound from headphones at all.


Was trying some fixes, tried to uninstall alsa all together and install it again, got some errors and now my system is not finding any sound devices (speakers or otherwise).

i ran 

```
ubuntu-bug audio

```

And this is what I get...
```
1748
ERROR: symptom script /usr/share/apport/symptoms/audio.py crashed:
Traceback (most recent call last):
  File "/usr/lib/python2.7/dist-packages/apport/ui.py", line 56, in thread_collect_info
    package = symb['run'](report, ui)
  File "/usr/share/apport/symptoms/audio.py", line 192, in run
    (package, card, isOutput, jack) = ask_jack_and_card(report, ui)
  File "/usr/share/apport/symptoms/audio.py", line 22, in ask_jack_and_card
    cards = parse_cards()
  File "/usr/share/apport/symptoms/_audio_data.py", line 301, in parse_cards
    cards = add_pa_cards(cards, pactl_parsed)
  File "/usr/share/apport/symptoms/_audio_data.py", line 188, in add_pa_cards
    for pa_card in pactlvalues['Card'].itervalues():
KeyError: 'Card'

```

Would appreciate some help with the matter. thx in advance

---

