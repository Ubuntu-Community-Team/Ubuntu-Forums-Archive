---
title: "Is this a problem with my python?"
date: 2012-07-11
forum: Multimedia Software
---

### Post by X_Splinter on 2012-07-11
[INDENT]So I was trying to watermark some jpg photos using Phatch and I always get the error "cannot identify image"

Here's a copy from the error log:

______________

Error 0:Unable to apply the action Watermark on image 'DSCF0425.JPG' on folder:
/home/x_splinter/Xbox360/Slim PCB

cannot identify image file

Action:{'fields': {'Horizontal Justification': 'Right',
            'Horizontal Offset': '-5%',
            'Mark': u'/home/x_splinter/Xbox360/360-Hq_logos_allsizes.psd',
            'Method': u'By Offset',
            'Offset': '5%',
            'Opacity': u'100',
            'Orientation': u'Normal',
            'Position': u'Bottom Right',
            'Vertical Justification': 'Bottom',
            'Vertical Offset': '-5%',
            '__enabled__': 'yes'},
 'label': 'Watermark'}

Traceback (most recent call last):
  File "/usr/share/phatch/phatch/core/api.py", line 614, in apply_action_to_photo
    photo = action.apply(photo, read_only_settings, cache)
  File "/usr/share/phatch/phatch/core/models.py", line 106, in apply
    photo.get_layer().apply_pil(self.pil, **values)
  File "/usr/share/phatch/phatch/core/pil.py", line 750, in apply_pil
    self.image = function(self.image, *arg, **keyw)
  File "/usr/share/phatch/phatch/actions/watermark.py", line 45, in watermark
    orientation, opacity)
  File "/usr/share/phatch/phatch/lib/imtools.py", line 274, in generate_layer
    mark = convert_safe_mode(open_image(mark))
  File "/usr/share/phatch/phatch/lib/imtools.py", line 106, in open_image
    return Image.open(uri)
[B]  File "/usr/lib/python2.7/dist-packages/PIL/Image.py", line 1980, in open
    raise IOError("cannot identify image file")
IOError: cannot identify image file[/B]
*[/INDENT]

---

