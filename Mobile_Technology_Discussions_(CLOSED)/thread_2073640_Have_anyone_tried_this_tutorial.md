---
title: "Have anyone tried this tutorial ?"
date: 2012-10-20
forum: Mobile Technology Discussions (CLOSED)
---

### Post by Q-ro on 2012-10-20
Hello everyone, i'm trying to follow the tutorials for a camera app located in []("http://developer.android.com/guide/topics/media/camera.html#custom-camera") ; the problem is that when i try and copy paste to my project, i get an error showing there is something wrong int he following code:

```
public void surfaceCreated(SurfaceHolder holder) {
        // The Surface has been created, now tell the camera where to draw the preview.
        try {
            mCamera.setPreviewDisplay(holder);
            mCamera.startPreview();
        } catch (IOException e) {
            Log.d(TAG, "Error setting camera preview: " + e.getMessage());
        }
    }
```

the error goes something like "TAG variable is not set", but, as far as i understood, TAG is some sort of internal class/function on the Android API, so, ¿ is there something i'm missing ?.

Thanks in advance.

---

### Post by mevun on 2012-10-20
I don't know about your tutorial, but your understanding of TAG is wrong.
Log.d uses the Log class which has a class function d (which stands for debug).
You pass to that function a 'tag' parameter which should be a String (or maybe a CharSequence or other similar class).  Obviously, the second parameter is also a String or CharSequence.

So you can put a line higher above like
TAG = "myApp";

---

### Post by Q-ro on 2012-10-20
oh i'm sorry about the tutorial site, i'm adding the address :

[http://developer.android.com/guide/topics/media/camera.html#custom-camera](http://developer.android.com/guide/topics/media/camera.html#custom-camera)

As for TAG, ¿so what you are saying is that TAG should be a string in my string.xml ?

---

### Post by Parker32 on 2012-11-12
I don't know about this and never used it before.

---

### Post by shahrulbig5 on 2012-11-28
am never tried it before... haha.. :D

[[spoiler=Cerita ane gan!]]("http://voolow.blogspot.com/2012/01/tips-sukses-interview-melamar-kerja.html") 
[[IMG]http://4.bp.blogspot.com/-LcopHOItIHA/UFBUJQZQLbI/AAAAAAAAB6k/29dpyIsXRUg/s400/voolow%2Blogoo%2Brgb%2B%2528FILEminimizer%2529.jpg[/IMG]]("http://voolow.blogspot.com/2011/12/ciri-ciri-anak-gaul-versi-tahun-2011.html")

[/spoiler]

---

