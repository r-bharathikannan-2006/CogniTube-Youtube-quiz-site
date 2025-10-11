# CogniTube ✨ - Dynamic YouTube Quiz Generator

CogniTube transforms passive video watching into an active learning experience. Simply search for any educational video on YouTube, and CogniTube will dynamically generate a multiple-choice quiz based on the video's content, helping you test and reinforce your knowledge on the spot.

---

## 🌐 Live Demo

You can try CogniTube live right now!

### [Click here to visit the live website](https://your-cognitube-project.onrender.com)

#### ⚠️ Please Note:

This project is hosted on **Render's free tier**. If the website hasn't been visited in a while, the server goes into a sleep mode to conserve resources.
As a result, your **first visit might take 30-60 seconds to load** while the server wakes up. Subsequent clicks and page loads will be much faster. Thank you for your patience!

---

## 🚀 Table of Contents

- [About The Project](#about-the-project)
- [Key Features](#key-features)
- [How It Works](#how-it-works)
- [Screenshots](#screenshots)
- [Built With](#built-with)
- [Getting Started](#getting-started)
  - [Prerequisites](#prerequisites)
  - [Installation & Setup](#installation--setup)
- [Usage](#usage)
- [Project Structure](#project-structure)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

---

## 📖 About The Project

In an age of endless online video content, truly retaining information can be a challenge. CogniTube was built to bridge the gap between watching and learning. It's a web application for students, professionals, and lifelong learners who want to actively engage with educational content. By generating quizzes directly from a video's transcript, it provides instant feedback and helps solidify key concepts.

---

## 🌟 Key Features

- **YouTube Video Search**: Seamlessly search for any video using the YouTube Data API.
- **Dynamic Quiz Generation**: Leverages the power of Google's Gemini AI to create relevant, concept-oriented multiple-choice questions from a video's transcript.
- **Interactive Learning**: Watch the video and take the quiz side-by-side for an integrated experience.
- **Instant Feedback**: Answers are checked in real-time, with correct answers highlighted to reinforce learning.
- **Simple & Clean UI**: A straightforward interface built with Tailwind CSS that focuses on the learning process.

---

## ⚙️ How It Works

The application follows a simple yet powerful workflow, handled by Django views and templates:

1. **Search**: The user visits the homepage (`search_template.html`), enters a topic in the search bar, and submits the form via a POST request.
2. **Fetch Videos**: The `search_template` view in `core/views.py` receives the query. It then calls the `search_video` function from `core/apis.py`, which uses the **YouTube Data API v3** to retrieve a list of relevant videos.
3. **Display Results**: The list of videos is passed to the `search_results.html` template, where each video is displayed with its thumbnail, title, and channel.
4. **Select Video**: The user clicks on a video, which navigates them to the URL `/player/<video_id>/`.
5. **Generate Quiz**: This URL is handled by the `open_player` view.
  - This view calls the `generate_questions` function from `core/apis.py` with the video's ID.
  - This function fetches the video's transcript and sends it as a prompt to the **Google Gemini API**.
  - Gemini processes the transcript and returns a structured set of multiple-choice questions.
6. **Learn**: The video ID and the generated questions are passed to the `video_player.html` template, which displays the YouTube video embed alongside the interactive quiz.

---

## 🛠️ Built With

This project is built with a modern Python web stack:

- **Backend**: [Django](https://www.djangoproject.com/)
- **Frontend**: [Tailwind CSS](https://tailwindcss.com/)
- **APIs**:
  - [Google Gemini API](https://ai.google.dev/) for AI-powered quiz generation.
  - [YouTube Data API v3](https://developers.google.com/youtube/v3) for video search.
- **Libraries**:
  - `requests`
  - `youtube-transcript-api`
  - `django`

---

## 🏁 Getting Started

To get a local copy up and running, follow these simple steps.

### Prerequisites

- Python 3.8+
- pip (Python package installer)
- Git

### Installation & Setup

1. **Clone the repository:**
  
  ```sh
  git clone [https://github.com/r-bharathikannan-2006/CogniTube-Youtube-quiz-site.git](https://github.com/r-bharathikannan-2006/CogniTube-Youtube-quiz-site.git)
  cd CogniTube-Youtube-quiz-site
  ```
  
2. **Install the required packages:**
  
  ```sh
  pip install -r requirements.txt
  ```
  
3. **Set up environment variables:**
  This project requires API keys to function. Create a `.env` file in the root directory of the project (the same directory as `manage.py`).
  
  ```
  touch .env
  ```
  
  Add your API keys to the `.env` file like this:
  
  ```env
  # .env file
  SEARCH_KEY=YOUR_YOUTUBE_DATA_API_KEY
  GEMINI_KEY=YOUR_GOOGLE_GEMINI_API_KEY
  ```
  
  > **Note**: These keys are loaded in `core/apis.py` using `os.getenv()`. Never commit your `.env` file to version control! The `.gitignore` file is already configured to ignore it.
  
4. **Apply database migrations:** ( Optional : As this project doesn't use DataBase )
  
  ```sh
  python manage.py migrate
  ```
  
5. **Run the development server:**
  
  ```sh
  python manage.py runserver
  ```
  
  The application will be available at `http://127.0.0.1:8000/`.
  

---

## 🖥️ Usage

1. Navigate to the live application at **[https://cognitube.onrender.com/](https://cognitube.onrender.com/)** or, if running locally, go to [http://127.0.0.1:8000/](http://127.0.0.1:8000/).
2. Enter a topic or keyword into the search bar and submit the form.
  - **Please note:** The initial search may take **8-10 seconds** as it fetches data from the YouTube API.
3. From the search results page, click on the video you want to study.
  - **Please be patient:** The video player and quiz page may take **15-20 seconds** to load. This is because the backend is fetching the video transcript and generating a brand new quiz using the Gemini AI in real-time.
4. Once loaded, you can watch the video on the left and answer the questions on the right to test your knowledge.

---

## 🙌 Contributing

Contributions are what make the open-source community such an amazing place to learn, inspire, and create. Any contributions you make are **greatly appreciated**.
If you have a suggestion that would make this better, please fork the repo and create a pull request. You can also simply open an issue with the tag "enhancement".

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

---

## 📧 Contact

Bharathikannan R - [r.bharathikannan.official@gmail.com]
Project Link : [https://github.com/r-bharathikannan-2006/CogniTube-Youtube-quiz-site.git](https://github.com/r-bharathikannan-2006/CogniTube-Youtube-quiz-site.git)

LinkedIn : [Linkedin - Bharathikannan R](https://www.linkedin.com/in/bharathikannan-r-1a955733b/)
