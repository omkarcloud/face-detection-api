![Face Detection API Featured Image](https://raw.githubusercontent.com/omkarcloud/face-detection-api/master/face-detection-api-featured-image.png)

# Face Detection API

Detect faces, bounding boxes, and five facial landmarks (eyes, nose, mouth corners) in any image via a simple REST API. Upload a JPEG or PNG, get structured JSON back. 100 free requests/month.

## Key Features

- Detect every face in an image with confidence scores
- Get normalized bounding boxes and five facial landmark coordinates per face
- Supports JPEG and PNG uploads up to 16 MB
- All coordinates normalized (0–1) — resolution-independent
- **100 requests/month on free tier**
- Example Response:
```json
{
  "image_width": 612,
  "image_height": 408,
  "total_faces": 2,
  "faces": [
    {
      "confidence": 0.9991222023963928,
      "bounding_box": {
        "origin_x": 0.7696828591947755,
        "origin_y": 0.07557892352342604,
        "span_width": 0.18395689328511555,
        "span_height": 0.27593533992767333
      },
      "landmarks": {
        "left_eye": { "x": 0.803, "y": 0.168 },
        "right_eye": { "x": 0.890, "y": 0.154 },
        "nose": { "x": 0.835, "y": 0.182 },
        "mouth_left": { "x": 0.808, "y": 0.264 },
        "mouth_right": { "x": 0.886, "y": 0.253 }
      }
    }
  ]
}
```

## Get API Key

Create an account at [omkar.cloud](https://www.omkar.cloud/auth/sign-up?redirect=/api-key) to get your API key.

It takes just 2 minutes to sign up. You get 100 free requests every month for face detection.

This is a well built product, and your search for the best Face Detection API ends right here.


## Quick Start

```bash
curl -X POST "https://face-detection-api.omkar.cloud/face/analyze" \
  -H "API-Key: YOUR_API_KEY" \
  -F "image=@photo.jpg"
```

```json
{
  "image_width": 612,
  "image_height": 408,
  "total_faces": 2,
  "faces": [
    {
      "confidence": 0.9991222023963928,
      "bounding_box": {
        "origin_x": 0.7696828591947755,
        "origin_y": 0.07557892352342604,
        "span_width": 0.18395689328511555,
        "span_height": 0.27593533992767333
      },
      "landmarks": {
        "left_eye": { "x": 0.8030567288398743, "y": 0.16781179904937743 },
        "right_eye": { "x": 0.889804744720459, "y": 0.15399449467658993 },
        "nose": { "x": 0.8354169130325317, "y": 0.18160911798477172 },
        "mouth_left": { "x": 0.8082399487495423, "y": 0.26384876668453217 },
        "mouth_right": { "x": 0.886027567088604, "y": 0.25258797258138654 }
      }
    }
  ]
}
```

## Quick Start (Python)

```bash
pip install requests
```

```python
import requests

response = requests.post(
    "https://face-detection-api.omkar.cloud/face/analyze",
    headers={"API-Key": "YOUR_API_KEY"},
    files={"image": open("photo.jpg", "rb")}
)

print(response.json())
```


## API Reference

### Face & Landmark Detection

```
POST https://face-detection-api.omkar.cloud/face/analyze
```

#### Parameters

| Parameter | Required | Default | Description |
|-----------|----------|---------|-------------|
| `image` | Yes | — | JPEG or PNG image file, sent as multipart form-data. Max 16 MB. |

#### Example

```python
import requests

response = requests.post(
    "https://face-detection-api.omkar.cloud/face/analyze",
    headers={"API-Key": "YOUR_API_KEY"},
    files={"image": open("photo.jpg", "rb")}
)

print(response.json())
```

#### Response

<details>
<summary>Sample Response (click to expand)</summary>

```json
{
  "image_width": 612,
  "image_height": 408,
  "total_faces": 2,
  "faces": [
    {
      "confidence": 0.9991222023963928,
      "bounding_box": {
        "origin_x": 0.7696828591947755,
        "origin_y": 0.07557892352342604,
        "span_width": 0.18395689328511555,
        "span_height": 0.27593533992767333
      },
      "landmarks": {
        "left_eye": { "x": 0.8030567288398743, "y": 0.16781179904937743 },
        "right_eye": { "x": 0.889804744720459, "y": 0.15399449467658993 },
        "nose": { "x": 0.8354169130325317, "y": 0.18160911798477172 },
        "mouth_left": { "x": 0.8082399487495423, "y": 0.26384876668453217 },
        "mouth_right": { "x": 0.886027567088604, "y": 0.25258797258138654 }
      }
    },
    {
      "confidence": 0.9932157397270203,
      "bounding_box": {
        "origin_x": 0.47802788168191923,
        "origin_y": 0.1437148481607437,
        "span_width": 0.23806619644165045,
        "span_height": 0.35709929466247564
      },
      "landmarks": {
        "left_eye": { "x": 0.5511994868516922, "y": 0.25441014766693115 },
        "right_eye": { "x": 0.6608513176441193, "y": 0.2665567696094513 },
        "nose": { "x": 0.608675591647625, "y": 0.3018725097179413 },
        "mouth_left": { "x": 0.5523210883140565, "y": 0.39049973487854 },
        "mouth_right": { "x": 0.6461554944515229, "y": 0.4011178731918335 }
      }
    }
  ]
}
```

</details>

## Error Handling

```python
response = requests.post(
    "https://face-detection-api.omkar.cloud/face/analyze",
    headers={"API-Key": "YOUR_API_KEY"},
    files={"image": open("photo.jpg", "rb")}
)

if response.status_code == 200:
    data = response.json()
elif response.status_code == 400:
    # Invalid image format or missing file
    pass
elif response.status_code == 401:
    # Invalid API key
    pass
elif response.status_code == 429:
    # Rate limit exceeded
    pass
```

## FAQs

### What data does the API return?

**Face & Landmark Detection** returns per image:
- Image dimensions (`image_width`, `image_height`)
- Total number of faces detected (`total_faces`)

Per face:
- Confidence score (0–1)
- Bounding box with origin coordinates and dimensions (`origin_x`, `origin_y`, `span_width`, `span_height`)
- Five facial landmarks: `left_eye`, `right_eye`, `nose`, `mouth_left`, `mouth_right` — each with normalized `x` and `y` coordinates

All coordinates are normalized between 0 and 1 relative to image dimensions. Multiply by `image_width` or `image_height` to get pixel values.

### How accurate is the data?

Deep learning model with over 99% confidence on clearly visible faces. Every API call runs inference in real time.

The model handles varied lighting, angles, and partial occlusions. Confidence scores tell you exactly how sure the model is about each detection.

### Are the coordinates in pixels?

No. All coordinates are normalized between 0 and 1. This makes them resolution-independent.

To convert to pixels, multiply `x` values by `image_width` and `y` values by `image_height`. For example, if `left_eye.x` is `0.803` and `image_width` is `612`, the pixel position is `612 × 0.803 ≈ 491`.

### Can it detect multiple faces?

Yes. The API detects every face in the image. A group photo with 10 people returns 10 face objects, each with its own bounding box, confidence score, and landmarks.

### What are the five landmarks?

1. **Left eye** — center of the left eye
2. **Right eye** — center of the right eye
3. **Nose** — tip of the nose
4. **Mouth left** — left corner of the mouth
5. **Mouth right** — right corner of the mouth

These five points are enough for face alignment, gaze estimation, expression analysis, and face-aware cropping.

## Rate Limits

| Plan | Price | Requests/Month |
|------|-------|----------------|
| Free | $0 | 100 |
| Starter | $16 | 3,000 |
| Grow | $48 | 15,000 |
| Scale | $148 | 75,000 |

## Questions? We have answers.

Reach out anytime. We will solve your query within 1 working day.

[![Contact Us on WhatsApp about Face Detection API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/whatsapp-us.png)](https://api.whatsapp.com/send?phone=918178804274&text=I%20have%20a%20question%20about%20the%20Face%20Detection%20API.)

[![Contact Us on Email about Face Detection API](https://raw.githubusercontent.com/omkarcloud/assets/master/images/ask-on-email.png)](mailto:happy.to.help@omkar.cloud?subject=Face%20Detection%20API%20Question)
