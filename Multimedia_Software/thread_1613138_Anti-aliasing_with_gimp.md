---
title: "Anti-aliasing with gimp"
date: 2010-11-04
forum: Multimedia Software
---

### Post by hotstepperk on 2010-11-04
Hello.

So I've been developing a website of late, and I've only just noticed that while images look nice and smooth on my browser (chrome) they look jagged in almost every other browser (Fire-fox, internet explorer, epiphany)

I'm looking for a way to make them smoother and view well- I believe its anti-aliasing. When I try and go to filters > enhanced, anti aliasing isn't an option.

Is there any way, then, I can make my images look more presentable for compatibility with other browsers? 

Thanks.

---

### Post by squaregoldfish on 2010-11-04
This isn't an issue I've seen with browsers in a long time, and I suspect that the fault isn't with the image, but more the HTML. Is it possible you're displaying the image at a fixed size that's different to the image size? Or even display the page zoomed in? If so, Chrome may be doing some smoothing of its own that the other browsers aren't bothering with.

Steve.

---

### Post by mcduck on 2010-11-04
I agree with squaregoldfish, all Gimp's tools already do antialiasing by default, and if the problem was in the image itself you'd see it regardless of what browser you use.

Defining a wrong image size in your code would give results like what you are seeing, forcing the browser to scale the image with variable results based on how well the browser does that.

---

### Post by hotstepperk on 2010-11-23
> **squaregoldfish said:**
> This isn't an issue I've seen with browsers in a long time, and I suspect that the fault isn't with the image, but more the HTML. Is it possible you're displaying the image at a fixed size that's different to the image size? Or even display the page zoomed in? If so, Chrome may be doing some smoothing of its own that the other browsers aren't bothering with.



Sorry for the late reply. I am indeed, but only chrome seems to be smoothing the images while firefox and even IE7 and IE8 can't. Do I then have to scale the images to be fixed at certain dimensions or smooth them somehow with gimp.

---

### Post by squaregoldfish on 2010-11-23
If you want your images to be displayed well at a certain size, you have to create them at that size in the first place. You can't expect browsers to do that work for you, even if one or two browsers happen to have that feature.

As mcduck said, GIMP's scaling tool will interpolate/smooth your image by default. However, the most accurate method is to re-create your images at the correct size from scratch.

Steve.

---

### Post by SeijiSensei on 2010-11-23
> **hotstepperk said:**
> Sorry for the late reply. I am indeed, but only chrome seems to be smoothing the images while firefox and even IE7 and IE8 can't. Do I then have to scale the images to be fixed at certain dimensions or smooth them somehow with gimp.

You should always include the height and width parameters in an <img> tag, and they should match the actual size of the image.  If you specify a different size than the actual image, the browser will scale or distort the image to fit in the specified area.

That said, there's nothing you can do if someone scales up the entire page with the Zoom command.  I use a large-screen TV as a monitor and usually have web pages zoomed up to 120% or more of their original sizes.  I'll see artifacting in images as a result, but it's my doing, not the website designer's fault.

---

