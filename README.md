# YouTube Transcript Scraper: Translate, No Login · $3/1K

Get the full transcript of any YouTube video **and the same transcript in up to 30 other languages, with the same timestamps**: plain text, timestamped segments, every subtitle track the creator uploaded, SRT/VTT files and basic video details, in one run. Paste one link or thousands.

**[Run it on Apify](https://apify.com/pomlabs/youtube-transcript-scraper?utm_source=github&utm_medium=readme&utm_campaign=youtube-transcript-scraper)**: no install, no login, free credit on a new Apify account.

## What you get

- **Translations with aligned timestamps** (`translateTo`, up to 30 languages): the creator's human subtitles when they exist, a machine translation otherwise, each marked with its source
- **Full transcript text**, ready for search, summaries, translation or LLM pipelines
- **Timestamped segments** (start, duration, text) for subtitles, chapters or clipping
- **Language control**: list your preferred languages; manual captions are chosen over auto-generated ones; if none of your languages exist, you still get the first available track instead of an empty result
- **Video details** at no extra cost: title, channel name and ID, view count, length, live flag, and the list of caption languages available
- **Clear status per video**: `ok`, `no_captions`, `unavailable`, `invalid_url` or `blocked`
- **Translations that actually arrive**: set `translateTo` (for example `["pt", "es", "ja"]`) and get the transcript in each language with the **same timestamps**. When the creator published subtitles in that language, you get the human version; otherwise a machine translation. Many YouTube scrapers return HTTP 429 or silently fall back to the original language here, because YouTube throttles its auto-translated captions; this Actor does not depend on that endpoint.
- **Every language the creator uploaded**: `allLanguages: true` returns all human subtitle tracks of the video (big channels often have 5 to 30), each with its source marked `creator`.
- **Ready subtitle files**: `subtitleFormat: "srt"` or `"vtt"` adds the file as text, for the transcript and for every extra language.
- **Any link format**: watch URLs, `youtu.be` links, Shorts, embed and live links, or bare 11-character video IDs. Duplicates are removed automatically.

## Pricing

**No login, no API key. You pay only for transcripts delivered: $0.003 per video ($3 per 1,000), plus $0.002 per extra language if you ask for translations.** Videos without captions, private or deleted videos, and invalid links are listed in the results with the reason, and are never charged.

That is the free-plan price; Apify paid plans (Bronze, Silver, Gold) pay less per item.

## Call it by API

```bash
curl -X POST "https://api.apify.com/v2/acts/pomlabs~youtube-transcript-scraper/run-sync-get-dataset-items?token=YOUR_APIFY_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"urls": ["https://www.youtube.com/watch?v=jNQXAC9IVRw", "https://youtu.be/dQw4w9WgXcQ"]}'
```

Python:

```python
from apify_client import ApifyClient

client = ApifyClient("YOUR_APIFY_TOKEN")
run = client.actor("pomlabs/youtube-transcript-scraper").call(run_input={"urls": ["https://www.youtube.com/watch?v=jNQXAC9IVRw", "https://youtu.be/dQw4w9WgXcQ"]})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Use it from Claude, Cursor or any MCP client

```bash
claude mcp add youtube-transcript "https://mcp.apify.com?tools=pomlabs/youtube-transcript-scraper" -t http
```

## Ready-made examples

- [Get a YouTube video transcript as plain text](https://apify.com/pomlabs/youtube-transcript-scraper/examples/youtube-transcript-plain-text)
- [Translate YouTube subtitles to Spanish (SRT)](https://apify.com/pomlabs/youtube-transcript-scraper/examples/translate-youtube-subtitles-to-spanish)
- [Export transcripts of several YouTube videos to CSV](https://apify.com/pomlabs/youtube-transcript-scraper/examples/youtube-transcripts-of-several-videos)

## More Actors by Pom Labs

- [LinkedIn Profile Scraper (No Cookies) + Similar Profiles](https://apify.com/pomlabs/linkedin-profile-scraper?utm_source=github&utm_medium=readme&utm_campaign=youtube-transcript-scraper)
- [Instagram Profile Scraper: Exact Followers, Reels Views](https://apify.com/pomlabs/instagram-profile-data?utm_source=github&utm_medium=readme&utm_campaign=youtube-transcript-scraper)
- [Video Downloader: TikTok No Watermark, Instagram, YouTube, X](https://apify.com/pomlabs/video-downloader?utm_source=github&utm_medium=readme&utm_campaign=youtube-transcript-scraper)
- [LinkedIn Company Scraper (No Cookies): Posts, Similar Companies](https://apify.com/pomlabs/linkedin-company-scraper?utm_source=github&utm_medium=readme&utm_campaign=youtube-transcript-scraper)
- [Threads Scraper: Keyword Search, Posts & Profiles · No Login](https://apify.com/pomlabs/threads-scraper?utm_source=github&utm_medium=readme&utm_campaign=youtube-transcript-scraper)
- [AliExpress Scraper: Exact Units Sold, Prices, Search · $1/1K](https://apify.com/pomlabs/aliexpress-scraper?utm_source=github&utm_medium=readme&utm_campaign=youtube-transcript-scraper)
- [Instagram Transcript Scraper: Reels, TikTok, Facebook, Hook](https://apify.com/pomlabs/social-video-transcript?utm_source=github&utm_medium=readme&utm_campaign=youtube-transcript-scraper)
- [Reddit Scraper: Deleted & Removed, Mods, Hidden Profiles](https://apify.com/pomlabs/reddit-posts-comments-scraper?utm_source=github&utm_medium=readme&utm_campaign=youtube-transcript-scraper)
- [YouTube Comments Scraper + Replies, Shorts · No API Key · $1/1K](https://apify.com/pomlabs/youtube-comments-scraper?utm_source=github&utm_medium=readme&utm_campaign=youtube-transcript-scraper)

Full documentation, input fields and output format: [YouTube Transcript Scraper: Translate, No Login · $3/1K on Apify](https://apify.com/pomlabs/youtube-transcript-scraper?utm_source=github&utm_medium=readme&utm_campaign=youtube-transcript-scraper).
