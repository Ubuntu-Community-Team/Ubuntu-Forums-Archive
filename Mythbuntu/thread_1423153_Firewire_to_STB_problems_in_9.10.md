---
title: "Firewire to STB problems in 9.10"
date: 2010-03-06
forum: Mythbuntu
---

### Post by scudderwagg on 2010-03-06
Hey folks,
A bit of a noob here.  I'm having some problems with my attempts to connect via firewire to a Comcast Motorola 6200 STB with Mythbuntu 9.10.  When I started to try to set it up, I got no GUID listed, so I went to the forums to find ways to troubleshoot.

I checked with plugreport and got no response at all.
Next I tried sudo modprobe raw1394 and got this back
```
WARNING: All config files need .conf: /etc/modprobe.d/ubuntu-repos.key.1, it will be ignored in a future release.
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 1: ignoring bad line starting with '-----BEGIN'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 2: ignoring bad line starting with 'Version:'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 4: ignoring bad line starting with 'mQGiBEmAYugRBACMQbuU/pdPoBveHqqaXBcj5PIVungTI5RdX+KrdvA6b4KcVZp7'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 5: ignoring bad line starting with 'cy64qmijePMQx9YzmRBgzdgig3YSJq3BEUC5/fKRSHKjMh9nWNGAMhNaGgOjzQhL'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 6: ignoring bad line starting with 'REE3/6a8GZHnFHdKank0SG+gpbYealKxs75sxxFLjmGQEiao0iDZXjIZ2wCglG2s'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 7: ignoring bad line starting with 'ilQJ0DPLHWM1y0hyZoZNm0cD+wQFj3u21NceQ2atF+GQFME3e9r/a6p0fVtHZRz2'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 8: ignoring bad line starting with 'EX4BJOoVsK7IpdCrWdzhzb1d39aBP7CvTiM4xj021l1xvcLhmZINMxOAryfZFKr0'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 9: ignoring bad line starting with 'Q5SPZgnFjFjAgatknnppmfJC0OY0yZpkbNc3dOZFAM789B1D66HJSYYUyS1cl8Ht'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 10: ignoring bad line starting with 'lh56A/9dMWdkanX6x5if75+bZieiuO+ePFeCVoUaCeLIYzTGQmz6MzlAqnlyFnVK'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 11: ignoring bad line starting with 'U6Y5sNk2qkKske9q0QMuPN9x+3NMGnVqMOy/32iT7/niB4ePXij93+pfSTguQzKr'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 12: ignoring bad line starting with 'etoMxddvV3g6l7ZN865kHPzpORZAKTV+xPyzwWKfCfMpFtEoMrRCSmVhbi1ZdmVz'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 13: ignoring bad line starting with 'IEF2ZW5hcmQgKFBhY2thZ2VzIFNpZ25pbmcgS2V5KSA8cmVnLWp5YS1ncGdAYXZl'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 14: ignoring bad line starting with 'bmFyZC5vcmc+iGYEExECACYFAkmAYugCGwMFCQPCZwAGCwkIBwMCBBUCCAMEFgID'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 15: ignoring bad line starting with 'AQIeAQIXgAAKCRBDxdfqY3Av01h8AJkBXHmO/SUI7I/vem91OF3Dm9vf7ACaA9Gw'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 16: ignoring bad line starting with 'ar9Lye+ritCs0YVA48p1DpS5Ag0ESYBi6BAIAOXAsS0zyqoLl9j0vj8hEILOwl1q'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 17: ignoring bad line starting with 'Ux1s19ZaNs4ETLY5GuHEo+MYgZdX3TbVeQcT6P91wBWRD/ELtG/9UK/cdoF/6u8u'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 18: ignoring bad line starting with 'FHJywkWJhqjd1iPtRAeE1VpC6WYgLP138Aq6UFYgDF5CP423Hzpbqgk7VI09P6uu'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 19: ignoring bad line starting with 'JQTiDrD5K+Yyx1elacVG5zf7JId9R/yaRyDFXHMCpXnwKsAFhLtKQLKoET7OfdOy'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 20: ignoring bad line starting with 'Aj/d2kuNO+AGaY4d3CHjRmFToI6RsSubC5fnRGap5drpi1sJ3SOuloQQ1jDC/hC1'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 21: ignoring bad line starting with 'wQrNvC30IlhaYFBZWA3vDEg08VDxup8UXhrU247mf4tiZaWrOkB0QgC2NS8AAwUI'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 22: ignoring bad line starting with 'ANNvVPpcC+UiauQ6KtckYww/tuBJvxfUThGHjxJECykQbIDakQL7Ew7cjGrfyn2o'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 23: ignoring bad line starting with 'WUYbXuG1YQK6e5qMSo/gsdY204ruTlEQoqVSeLFwrbtGiIo4yIRuARDsbqtsMj/f'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 24: ignoring bad line starting with 'k9w3HW5bg9HwpUl1CWUqIU3OOmvavTMFGp2uYKGCspjQ8GQ9Q75PJ/OxoNfE65/p'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 25: ignoring bad line starting with 'p2ZHGHL+kI5UtHiXFtfAYqMiVOJhVxuRkVTF4N6lI5Eo3RKXIXRzkgikWL0tkoK0'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 26: ignoring bad line starting with 'LAKOvXrCN9DzRJaqbjKum07S+e1Hexl9JeZtaPqUzfcGGcqJ6hz7q8cR/KqdaAOW'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 27: ignoring bad line starting with 'keoprtRgbDXMBpEw4+vqQFqITwQYEQIADwUCSYBi6AIbDAUJA8JnAAAKCRBDxdfq'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 28: ignoring bad line starting with 'Y3Av03DrAJsH3nC3u9io+yYVhRNSZSj0QQ42zgCgi3HJhO4EMb3GdXeO9XIGxA5C'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 29: ignoring bad line starting with 'zLU='
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 30: ignoring bad line starting with '=MPwv'
WARNING: /etc/modprobe.d/ubuntu-repos.key.1 line 31: ignoring bad line starting with '-----END'
```
After that, though, I tried plugreport and got
```
Host Adapter 0
==============
```
There are two ports on my STB and two on my system.  I have tried all combinations of both, with no change in plugreport.  I have a SYBA 1394 card ([http://www.newegg.com/Product/Product.aspx?Item=N82E16815124034](http://www.newegg.com/Product/Product.aspx?Item=N82E16815124034)) which should work; comments at Newegg suggest it woks fine with linux.  I have checked the diagnostics on the box and they show the Firewire port as on and the channel I am tuned to has no 5C protection.

Also, just in case it matters, I enabled the weekly autobuilds for 0.22 and then upgraded the nvidia drivers to 195 using javenyard's repositories and upgraded and patched ALSA per [http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240&redirect=no](http://wiki.xbmc.org/index.php?title=HOW-TO_set_up_HDMI_audio_on_nVidia_GeForce_G210,_GT220,_or_GT240&redirect=no).  All of that was to get my GT220 working to pass the audio via HDMI, which it is doing.

Any help would be greatly appreciated.  Thanks.

---

### Post by scudderwagg on 2010-03-06
Ha, well forget the question, it was a hardware problem.  Picked up a new PCI Firewire card and it worked just fine.  VIA chipset screws me again.  I am really starting to hate those guys.

---

