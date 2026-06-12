---
title: "GIMP batch process script run-time error"
date: 2014-04-06
forum: Multimedia Software
---

### Post by Paddy Landau on 2014-04-06
I need a bit of help, please, with scripting a batch process for GIMP. I hope that I'm asking on the right forum; if there is a better place to ask, please point me in the right direction. (I'm an absolute beginner when it comes to GIMP scripting.)

I have a bunch of images that I wish to process with [script-fu-pencil-drawing]("http://registry.gimp.org/node/22018"). For simplicity's sake, I'll talk about just a single image in this post.

I have used the [tutorial for GIMP batch scripting]("http://www.gimp.org/tutorials/Basic_Batch/"). Taking the tutorial's example verbatim works perfectly. But when I adjust the script for [FONT=lucida console]script-fu-pencil-drawing[/FONT], I get an error.

Note that [FONT=lucida console]script-fu-pencil-drawing[/FONT] works when used interactively; it is only when used in this batch script that it fails.

Here is the script as I've adjusted it. The changes are highlighted.
```
(define (simple-[COLOR=#000080]**script-fu-pencil-drawing**[/COLOR] filename
                                         [COLOR=#000080]**radius**[/COLOR]
                                         [COLOR=#000080]**strength**[/COLOR]
                                         [COLOR=#000080]**mergelayers**[/COLOR])
   (let* ((image (car (gimp-file-load RUN-NONINTERACTIVE filename filename)))
          (drawable (car (gimp-image-get-active-layer image))))
          ([COLOR=#000080]**script-fu-pencil-drawing**[/COLOR] RUN-NONINTERACTIVE
                                    image drawable [COLOR=#000080]**radius strength mergelayers**[/COLOR])
     (gimp-file-save RUN-NONINTERACTIVE image drawable filename filename)
     (gimp-image-delete image)))
```
Here is the command that I run on the command line, where [FONT=lucida console]foo.png[/FONT] is the image to be processed. Again, changes are highlighted.
```
gimp -i -b '(simple-[COLOR=#000080]**script-fu-pencil-drawing**[/COLOR] "foo.png" [COLOR=#000080]**8.0 16.0 TRUE**[/COLOR])' -b '(gimp-quit 0)'
```
Here is the output. The original [FONT=lucida console]foo.png[/FONT] is left unchanged.
```
GIMP-Error: Calling error for procedure 'gimp-layer-copy':
Procedure 'gimp-layer-copy' has been called with an invalid ID for argument 'layer'. Most likely a plug-in is trying to work on a layer that doesn't exist any longer.

batch command experienced an execution error:
Error: ( : 1) Procedure execution of gimp-layer-copy failed on invalid input arguments: Procedure 'gimp-layer-copy' has been called with an invalid ID for argument 'layer'.
Most likely a plug-in is trying to work on a layer that doesn't exist any longer.
```
I have been at this for a couple of hours, and nothing that I've tried has worked. If you could help me fix this, please, I would be most grateful.

---

### Post by Paddy Landau on 2014-04-23
Someone [gave me the solution]("http://gimpforums.com/thread-gimp-batch-process-script-run-time-error"), in case this helps anyone else with this problem.

---

