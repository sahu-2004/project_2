from transformers import pipeline

# Load the sentiment analysis model
sentiment_pipeline = pipeline("sentiment-analysis")

def analyze_sentiment(text):
    result = sentiment_pipeline(text)[0]
    label = result['label']
    score = result['score']
    return label, score

def main():
    print("=== AI Sentiment Analyzer ===\n")
    while True:
        user_input = input("Enter text (or 'q' to quit): ").strip()
        if user_input.lower() == 'q':
            break
        if user_input:
            label, confidence = analyze_sentiment(user_input)
            print(f"Sentiment: {label} (Confidence: {confidence:.2f})\n")
        else:
            print("Please enter valid text.\n")

if __name__ == "__main__":
    main()
