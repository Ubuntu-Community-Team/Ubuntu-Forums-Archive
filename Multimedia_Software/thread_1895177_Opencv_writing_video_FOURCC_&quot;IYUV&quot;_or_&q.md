---
title: "Opencv writing video FOURCC &quot;IYUV&quot; or &quot;I420&quot;"
date: 2011-12-14
forum: Multimedia Software
---

### Post by Hetepeperfan on 2011-12-14
Dear community,

To see the intermediate results of my  videooprocessing using opencv2.3.1 I used a videowriter to see my  results when my program ended.  I was very used to write frames using a  cv::videowriter( string filename, int fourcc, int fps. I used the codec  with the FOURCC codec "IYUV" or "I420" since it is able to write fast to  a file. In the example below I also present the code example below I'll  show a piece of  code with "MJPG" FOURCC, however in my program that  runs in realtime my system can't keep up if it has to write and compress  it to MJPG. Writing with codec "IYUV" used to work perfectly but just  seemed to fail last week over night. The writer is writing to a file  with all kind of codecs mentioned above, however when writing with IYUV  or I420 (which I think are synonemous) the resulting video looks  screwed.

I get these results on Ubuntu 10.10 and 10.04. opencv2.3.1 is build from source.

below I'll give a sample program that demonstrates the problem with a simple webcam.
If compiled with:
```
$g++ -o writer capture_writing.cpp `pkg-config --cflags --libs opencv`
```The writer will make a perfectly file output.avi file that I can investigate with mplayer of the default movieplayer.

however if compiled with:
```
$g++ -o writer capture_writing.cpp `pkg-config --cflags --libs opencv`  -D PROBLEM 
```it  starts to write to output.avi like nothing is wrong, however when  viewing the file with any video player the colors are mixed up I only  see a small piece of the total frame It shows stars and stripes, however  I'm not filming the American national flag but just myself.

capture_writing.cpp
is:

```
#include <iostream>

#include <cv.h>
#include <highgui.h>

using namespace cv;
using namespace std;

int main()
{
    VideoCapture cap (0);
    cap.set(CV_CAP_PROP_FRAME_WIDTH, 640);
    cap.set(CV_CAP_PROP_FRAME_HEIGHT, 480);

    Mat mat;
    cap >> mat;

    //cout << "The fps = " << cap.get(CV_CAP_PROP_FPS) << endl;

    VideoWriter writer( "output.avi",
#ifdef PROBLEM
            CV_FOURCC('I','4','2','0') ,
#else
            CV_FOURCC('M','J','P','G') ,
#endif
            30,
            Size(mat.size())
            );

    if ( !writer.isOpened()){
        cout << "couldn't open writer" << endl;
        return 1;
    }

    namedWindow("win",1);

    while ( (short) waitKey( 20 ) != 'q'){
        Mat mattie;
        cap >> mattie;
        writer << mattie;
        imshow("win",mattie);
    }

    return 0;
}
```Has anyone perhaps any idea why writing with IYUV or I420 is not working anymore?
any help is very welcome.

kind regards,

Maarten

---

### Post by Hetepeperfan on 2011-12-21
Nobody has been able to help me yet, is it perhaps an idea to move this thread to Multimedia & Video I was doubting when I posted this thread which of the two was the most appropriate?

Maarten

---

### Post by howefield on 2011-12-21
> **Hetepeperfan said:**
> is it perhaps an idea to move this thread to Multimedia & Video

Thread moved to "*Multimedia & Video*" forum.

Feel free to bump every 24 hours or so, sometimes it takes that persistent effort to catch the eye of someone who can help.

---

### Post by Hetepeperfan on 2011-12-21
> **howefield said:**
> Thread moved to "*Multimedia & Video*" forum.

Feel free to bump every 24 hours or so, sometimes it takes that persistent effort to catch the eye of someone who can help.

OK Thanks!

Maarten

---

### Post by Hetepeperfan on 2011-12-23
bump

---

