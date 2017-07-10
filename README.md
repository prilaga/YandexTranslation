# Yandex Translation

Simple util which helps to implement Yandex translation service with RxJava.

### Android Application Development
http://prilaga.com

Example of using:

### 1. Setup
        String sourceText = "Годный переводчик";
        String sourceLang = "ru";
        String destinationLang = "en";
        String key = "your_key";
        YandexTranslation translation = new YandexTranslation();

### 2. Get a text asynchronously:

        translation.setKey(key)
                .getTextObservable(sourceText, sourceLang, destinationLang)
                .subscribeOn(Schedulers.io())
                .observeOn(AndroidSchedulers.mainThread())
                .subscribe(new Observer<String>() {
                    @Override
                    public void onCompleted() {

                    }

                    @Override
                    public void onError(Throwable e) {

                    }

                    @Override
                    public void onNext(String text) {

                    }
                });
                
### 3. Get a Translation object asynchronously:

           translation.setKey(key)
                .getTranslationObservable(sourceText, sourceLang, destinationLang)
                .subscribeOn(Schedulers.io())
                .observeOn(AndroidSchedulers.mainThread())
                .subscribe(new Observer<YandexTranslation.Translation>() {
                    @Override
                    public void onCompleted() {

                    }

                    @Override
                    public void onError(Throwable e) {

                    }

                    @Override
                    public void onNext(YandexTranslation.Translation t) {

                    }
                });
                
### 4. Get a Translation in the same thread:  

     Translation translation = getTranslation(sourceText, sourceLang, destinationLang);
     
      if (YandexTranslation.Translation.hasTranslation(translation)){
          String text = translation.translations.get(0);
      }

                
