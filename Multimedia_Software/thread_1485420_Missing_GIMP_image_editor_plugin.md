---
title: "Missing GIMP image editor plugin"
date: 2010-05-16
forum: Multimedia Software
---

### Post by nocturnal1 on 2010-05-16
I'm trying to create a button in GIMP Image Editor in Ubuntu Intrepid.
File->Create->Buttons->Simple Beveled Button.

 This button is to be used in a Glade/GTK+ application. I will select the text to go on  it using Glade so I don't want text when creating it with GIMP. If I create the button without entering test I get the error:

Error while executing script-fu-button00:
Error: Procedure execution of gimp-layer-set-offsets failed on invalid input arguments: Procedure 'gimp-layer-set-offsets' has been called with an invalid ID for argument 'layer'. Most likely a plug-in is trying to work on a layer that doesn't exist any longer.

How can I fix this? I'm very new Ubuntu.

Thanks

---

